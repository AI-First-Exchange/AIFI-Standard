✅ AIFI v0 Minimal Profile (SDA + Canonical Integrity)

Status: LOCKED (v0)
Verification Tier: SDA only
Integrity Model: sha256 + canonical_excludes_self

This document defines the minimum required structure for an AIFI package to be considered valid in AIFX v0.

AIFI is a container for AI-generated images, bundling:

	•	manifest.json
	•	exactly one primary image in assets/
	•	canonical integrity hashes

⸻

1) Container Structure (.aifi)

An .aifi file is a ZIP container with:

Required:

	•	manifest.json
	•	assets/image.<ext> (single primary image)

Allowed extensions:

	•	.png
	•	.jpg
	•	.jpeg
	•	.webp

Exactly one image is required.

Security requirements:

	•	No symlinks
	•	No absolute paths
	•	No .. traversal

⸻

2) Manifest Required Fields

manifest.json MUST be valid JSON and MUST include:

Identity / Work

	•	aifx_version (string; current tooling uses "0.1")
	•	type = "AIFI"
	•	work.title (string; non-empty)

Creator (SDA)

	•	creator.name (string; non-empty)
	•	creator.contact (string; non-empty)

Provenance Scope

	•	mode (string; example: human-directed-ai)
	•	verification_tier MUST be "SDA"
	•	ai_generated MUST be true
	•	declaration (string; non-empty; human-authored)

Integrity

	•	integrity object MUST be present

⸻

3) Canonical Integrity (AIFX)

AIFI MUST include the canonical integrity block:
```json
"integrity": {
  "algorithm": "sha256",
  "manifest_hash_mode": "canonical_excludes_self",
  "hashed_files": {
    "assets/image.png": {"sha256": "<sha256>"},
    "manifest.json": {"sha256": "<manifest_hash>"}
  }
}
```
Rules

	•	integrity.algorithm MUST be "sha256"
	•	integrity.manifest_hash_mode MUST be "canonical_excludes_self"
	•	hashed_files MUST include:
	•	the primary image asset
	•	manifest.json

⸻

4) Canonical Manifest Hash Rule

The manifest.json hash MUST be computed as follows:

	1.	Remove integrity.hashed_files["manifest.json"]
  
	2.	Canonical JSON encode using:
  	  •	sort_keys = true
	  •	separators = (",", ":")
	  •	ensure_ascii = false
  
 	 3.	Compute SHA256 of canonical byte
  	 4.	Insert the resulting hash back into:
     
	  •	integrity.hashed_files["manifest.json"]

No file-byte hashing.
No whitespace hashing.
No circular hashing.

⸻

5) Validation Outcomes

A package MUST FAIL if:

	•	manifest.json missing
	•	More than one image present
	•	Image not under assets/
	•	Unsupported extension
	•	Required fields missing
	•	integrity missing
	•	algorithm != sha256
	•	manifest_hash_mode != canonical_excludes_self
	•	Any hash mismatch
	•	Unsafe paths or symlinks

⸻

6) v0 Scope Boundary

AIFI v0 does not:

	•	Prove authorship
	•	Verify identity
	•	Score trust
	•	Enforce copyright
	•	Enforce licensing

It only enforces:

	•	Structure
	•	SDA boundary
	•	Canonical integrity

⸻

Core Principle

Declare only what you can prove today.
Design for what you can verify tomorrow.

⸻

🎯 Result

Now:

	•	AIFM Minimal Profile
	•	AIFV Minimal Profile
	•	AIFI Minimal Profile

All follow the same structure:

	1.	Container
	2.	Manifest fields
	3.	Integrity
	4.	Hash rule
	5.	Validation outcomes
	6.	Scope boundary

That’s spec parity.
