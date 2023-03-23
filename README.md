# Strapi Image Transfer SPIKE

### Questions:
- Can Import Export Entries plugin be modified to match media files by filename ignoring hash and id?
- Can Media Library be extended to have "smart batch upload" functionality?
    - User would upload file(s) or folder
        - Each upload would be searched for in the media library for an existing matching asset
            - If matching asset found then it would be updated with new file content
            - Else new asset is created
- Will such functionalities work with the Strapi s3 upload provider?

### Findings:
- Strapi process can be attached to and debugged with breakpoints in vscode (see launch configurations in .vscode)
- Import Export Entries code seems to already try to match by id, hash, name, then url. (See `import-export-entries/server/services/import/utils/file.js:52`)
    - Need to test/confirm this behavior, as it is not what we were experiencing
        - The disconnect in expected behavior may be that although current ImportExportEntries plugin can find a file by name, the relation is still attempted using the original id, instead of the new found file's id