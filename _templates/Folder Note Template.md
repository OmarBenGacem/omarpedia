<%*
const folderPath = tp.file.folder(true) || "";
const folderParts = folderPath.split("/").filter(Boolean);
const baseFolderName = folderParts.length ? folderParts[folderParts.length - 1] : tp.file.title;

const canvasFolder = "_folder-canvas";
const canvasTemplatePath = "_templates/folder-note-canvas-template.canvas";
const targetCanvasPath = `${canvasFolder}/${baseFolderName}.canvas`;

function normalizeTag(tag) {
  return String(tag).replace(/^#/, "").trim();
}

async function ensureFolderExists(path) {
  if (!app.vault.getAbstractFileByPath(path)) {
    await app.vault.createFolder(path);
  }
}

function collectDescendantMarkdownFiles(currentFolderPath, currentFilePath) {
  const prefix = currentFolderPath ? `${currentFolderPath}/` : "";
  return app.vault.getMarkdownFiles().filter(file => {
    if (!prefix) return file.path !== currentFilePath;
    return file.path.startsWith(prefix) && file.path !== currentFilePath;
  });
}

const currentFilePath = tp.file.path(true);
const descendantFiles = collectDescendantMarkdownFiles(folderPath, currentFilePath);

const tagSet = new Set();

for (const file of descendantFiles) {
  const cache = app.metadataCache.getFileCache(file) || {};

  const fmTags = cache.frontmatter?.tags;
  if (Array.isArray(fmTags)) {
    for (const tag of fmTags) {
      const cleaned = normalizeTag(tag);
      if (cleaned) tagSet.add(cleaned);
    }
  } else if (typeof fmTags === "string") {
    for (const tag of fmTags.split(",")) {
      const cleaned = normalizeTag(tag);
      if (cleaned) tagSet.add(cleaned);
    }
  }

  if (Array.isArray(cache.tags)) {
    for (const tagObj of cache.tags) {
      const cleaned = normalizeTag(tagObj.tag);
      if (cleaned) tagSet.add(cleaned);
    }
  }
}

const sortedTags = [...tagSet].sort((a, b) => a.localeCompare(b));
const tagsYaml = sortedTags.length
  ? `tags:\n${sortedTags.map(tag => `  - ${tag}`).join("\n")}`
  : `tags: []`;

await ensureFolderExists(canvasFolder);

if (!app.vault.getAbstractFileByPath(targetCanvasPath)) {
  let canvasContent = JSON.stringify({ nodes: [], edges: [] }, null, 2);
  const templateFile = app.vault.getAbstractFileByPath(canvasTemplatePath);

  if (templateFile) {
    canvasContent = await app.vault.cachedRead(templateFile);

    // Placeholder replacements for future canvas templates
    canvasContent = canvasContent
      .replace(/\{\{folder-name\}\}/g, baseFolderName)
      .replace(/\{\{folder-path\}\}/g, folderPath)
      .replace(/\{\{topic-area\}\}/g, baseFolderName);
  }

  await app.vault.create(targetCanvasPath, canvasContent);
}
-%>
---
"Topic area": "<% baseFolderName %>"
<% tagsYaml %>
canvas: "[[<% targetCanvasPath %>|<% baseFolderName %>]]"
---
# Topics
%% Error: Cannot create a waypoint in the root folder of your vault. For more information, check the instructions [here](https://github.com/IdreesInc/Waypoint) %%
