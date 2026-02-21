AIFI — AI First Image Format (.aifi)
Part of the AI First Exchange (AIFX)

AIFI (AI First Image Format) is an open, ZIP-based standard for AI-generated images. It packages the image, prompts, generation parameters, model information, variations, licensing, and declared provenance into a single .aifi file designed for transparent, inspectable, and exchangeable AI-native image workflows.

AIFI is the image-level format in the AIFX family, enabling consistent documentation and interoperability across AI art tools, platforms, and archives.

🧩 Relationship to AIFX

AIFI is part of the AI First Exchange (AIFX) family of AI-native formats:

AIFM — AI First Music (.aifm)

AIFV — AI First Video (.aifv)

AIFI — AI First Image (.aifi)

AIFP — AI First Project (.aifp)

AIFI may be used standalone or embedded within an AIFP container as part of a larger multi-asset project.

🎨 Overview

An .aifi file represents a single AI-generated image with structured context.
It may include:

the final image asset

generation prompts and negative prompts

parameter settings (seed, steps, guidance, resolution, etc.)

model or engine identifiers

optional variations or upscales

licensing information

declared provenance and timestamps

AIFI prioritizes metadata transparency and workflow documentation, without asserting guarantees beyond the recorded creation process.

📦 AIFI Container Structure

An .aifi file is a ZIP container with the following standardized layout:
```
/
  manifest.json                 # REQUIRED: primary image manifest
  image/
    main.png                    # REQUIRED: primary image (png/jpg/webp)
    layers/                     # OPTIONAL: separated layers
    variations/                 # OPTIONAL: alternate renders or upscales
  prompts/
    generation.txt              # OPTIONAL: primary prompt
    negative.txt                # OPTIONAL: negative prompt
    metadata.json               # OPTIONAL: seed, steps, CFG, etc.
  model/
    model_info.json             # OPTIONAL: engine / model details
  legal/
    license.txt                 # OPTIONAL: licensing terms
    terms.txt                   # OPTIONAL
  extra/
    notes.md                    # OPTIONAL: creator notes
```

The manifest.json defines declared provenance, metadata references, and file paths.

🧠 Key Capabilities
✔ AI-Native Metadata Preservation

AIFI may preserve declared generation details such as:

prompt and negative prompt

seed value (where available)

sampler / guidance settings

steps and resolution

AI model or engine identifier

declared generation platform

creation timestamp

These fields support inspection, comparison, and archival workflows.

✔ Single-File Image Exchange

A single .aifi container may include:

final image

prompts and parameters

model references

variations or upscales

licensing and creator metadata

This makes AIFI suitable for sharing, archiving, and platform ingestion.

✔ Declared Provenance & Attribution

AIFI enables documentation of:

who declared authorship

what tools were used

under what parameters

when the image was generated

AIFI records declared provenance and metadata integrity.
It does not assert absolute origin beyond the documented workflow.

✔ Open & Extensible Design

AIFI is:

ZIP-based

JSON-driven

tool-agnostic

forward-compatible

Developers may extend AIFI to support:

new models

layered image systems

dataset labeling

editorial or licensing pipelines

📑 manifest.json (Simplified Example)
```
{
  "aifi_version": "1.0.0",
  "id": "aifi-2025-000001",
  "title": "Sample Image",
  "creator": "CreatorName",
  "resolution": "1024x1024",
  "format": "png",
  "ai_generated": true,

  "ai_source": {
    "tool_name": "Stable Diffusion",
    "model_name": "SDXL",
    "prompt_source": "prompts/generation.txt",
    "negative_prompt_source": "prompts/negative.txt",
    "settings_source": "prompts/metadata.json"
  },

  "provenance": {
    "creator_handle": "YourName",
    "creation_utc": "2025-12-05T12:00:00Z",
    "tool_chain": ["SDXL", "AIFX Converter v1.0"]
  },

  "files": {
    "main_image": "image/main.png",
    "variations": [
      "image/variations/upscale_1.png"
    ],
    "layers": [],
    "license_file": "legal/license.txt"
  }
}
```

Future versions may optionally include:

persona

verification_tier

signature

integrity_hash

🌐 MIME Type

Proposed MIME type:

image/aifi

🛠 Tooling (Planned)

Planned AIFI utilities:

aifiwrap — package image + metadata into .aifi

aifi-validate — validate files against the spec

aifi-core — libraries for reading/writing AIFI containers

🛠 Use Cases

AI art platforms

Editorial review and attribution

Dataset documentation

Layered image workflows

Long-term archival of prompt history

Licensing and compliance pipelines

🔄 Versioning

AIFI follows semantic versioning:

1.x.x — backward-compatible enhancements

2.x.x — backward-incompatible schema changes

Unknown fields should be safely ignored to maintain compatibility.

📬 Contributing

AIFI is an open specification under the AI First Exchange.

Contributions via issues and pull requests are welcome.

📝 License

This specification is released under the MIT License.
