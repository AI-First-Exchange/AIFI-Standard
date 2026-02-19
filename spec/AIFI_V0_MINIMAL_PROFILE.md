# AIFI v0 Minimal Profile (Desktop v0)

Status: LOCKED  
Verification Tier: SDA only  
Integrity Model: Canonical SHA256 (canonical_excludes_self)

---

## Purpose

This document defines the AIFI v0 Minimal Profile implemented by aifx-desktop.

It represents the first enforceable, deterministic version of AIFI.

---

## Container Structure (.aifi)

Zip root must contain:

manifest.json  
assets/image.<ext>

Allowed extensions:
- .png
- .jpg
- .jpeg
- .webp

Exactly one image is required.

---

## Required Manifest Fields

{
  "aifx_version": "0.1",
  "type": "AIFI",
  "work": {
    "title": "<string>"
  },
  "creator": {
    "name": "<string>",
    "contact": "<string>"
  },
  "mode": "<string>",
  "verification_tier": "SDA",
  "ai_generated": true,
  "declaration": "<string>",
  "integrity": { ... }
}

---

## Integrity Requirements

manifest.integrity.algorithm = "sha256"  
manifest.integrity.manifest_hash_mode = "canonical_excludes_self"

hashed_files MUST include:
- assets/image.<ext>
- manifest.json

Example:

"integrity": {
  "algorithm": "sha256",
  "manifest_hash_mode": "canonical_excludes_self",
  "hashed_files": {
    "assets/image.png": { "sha256": "<hash>" },
    "manifest.json": { "sha256": "<hash>" }
  }
}

---

## Canonical Manifest Hash Rule

The manifest.json hash MUST be computed as:

1. Remove integrity.hashed_files["manifest.json"]
2. Canonical JSON encode:
   - sort_keys = true
   - separators = (",", ":")
   - ensure_ascii = false
3. SHA256 of canonical bytes

No file-byte hashing.
No whitespace hashing.
No circular hashing.

---

## Validator Requirements

Validator MUST fail if:

- manifest.json missing
- More than one image present
- Image outside assets/
- Unsupported extension
- integrity missing
- algorithm != sha256
- manifest_hash_mode != canonical_excludes_self
- Any hash mismatch
- Required fields missing

Validator MUST NOT:

- Prove authorship
- Verify identity
- Score trust
- Enforce copyright

---

## Relationship to Full AIFI Specification

This Minimal Profile is a subset of the broader AIFI vision.

Future profiles may include:
- prompts/
- model metadata
- generation parameters
- layered assets

The Minimal Profile exists to ensure deterministic enforcement
before expanding scope.
