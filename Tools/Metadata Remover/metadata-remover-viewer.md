# Metadata Remover Viewer

[Metadata Remover Viewer](https://metadataremover.ai/metadata-viewer) is a free, read-only browser tool for inspecting metadata embedded in JPG/JPEG, PNG, and WebP images. The selected file and extracted values stay in the browser; the source file is not overwritten.

## Supported scope

- JPG/JPEG: supported EXIF, GPS, XMP, IPTC, comments, ICC profiles, and JUMBF markers.
- PNG: text chunks, EXIF, XMP-like packets, ICC profiles, supported AI workflow data, and caBX markers.
- WebP: EXIF, XMP, ICC profiles, animation state, and supported provenance markers.
- Supported images up to 25 MB.
- JSON, CSV, and PDF report exports.
- Direct HEIC/HEIF, AVIF, video, audio, Office documents, and PDFs are outside this image viewer's scope.

## How to use it

1. Open the viewer and select the exact JPG/JPEG, PNG, or WebP image to inspect.
2. Review the location, capture, identity, AI workflow, provenance, and file-structure groups.
3. Use search and filters to locate fields, then compare readable values with their raw representations.
4. Export a JSON, CSV, or PDF report when an audit record is useful.
5. Preserve the original file and corroborate important findings with ExifTool or another independent parser.

## Interpreting the results

- Missing metadata does not prove that an image is original, human-made, or unedited.
- Metadata may be stripped, changed, incomplete, or forged.
- A supported C2PA/JUMBF marker is not signature or trust-chain validation.
- The viewer does not perform pixel-level authenticity analysis or AI-image classification.
- Treat metadata as one signal and corroborate it with provenance and content/context.

## Privacy and evidence handling

- Inspection is local and read-only; the selected file is not uploaded to MetadataRemover.ai.
- Work from a copy when preserving forensic evidence.
- Record the source and a cryptographic hash separately when chain of custody matters.
- Treat exported reports as potentially sensitive because they may contain location, device, creator, or workflow data.
