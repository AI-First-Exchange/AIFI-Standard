# AI FORMAT FOUNDATION — VERIFICATION SPECIFICATION  
Version 1.0 • 2025  
Applies to: AIM, AIV, AII, AIP Standards

---

## 1. Purpose of Verification
The purpose of the AI Format Verification System (AFF-VS) is to establish **trust levels** for AI-generated media by documenting the source, human involvement, and authenticity of metadata. This specification introduces three verification tiers, badge definitions, manifest fields, and validation rules.

The Verification System ensures:
- Transparency of content origin  
- Authenticity of creator identity  
- Reliability of metadata  
- Ecosystem-wide trust signaling  
- Future compatibility with platform APIs  

---

## 2. Verification Tiers

### 🟡 **Tier 1 — Self-Declared Authenticity (SDA)**
**Badge:** 🟡 SDA  
**Trust Level:** Low  

Requirements:
- Creator manually enters metadata  
- No email or identity verification  
- No platform confirmation  

Intended for:
- Early-stage creators  
- Offline workflows  
- Simple conversions  

#### Manifest Fields Required:
"verification": {
"trust_level": "self-declared",
"method": "manual-entry",
"verified_email": false,
"platform_api": false,
"signature": null
}

---

### 🔵 **Tier 2 — Verified Creator (VC)**
**Badge:** 🔵 VC  
**Trust Level:** Medium

Requirements:
- Verified email  
- Human-authorship statement signed  
- Optional OAuth login (Google/GitHub/etc.)  
- SHA-256 hash signature stored in manifest  

Intended for:
- Professional creators  
- Monetization eligibility  
- Portfolio building  

#### Manifest Fields Required:
"verification": {
"trust_level": "creator-verified",
"method": "email-and-signature",
"verified_email": true,
"platform_api": false,
"signature": "sha256-hash-of-authorship-statement"
}

---

### 🟢 **Tier 3 — Platform Verified Authenticity (PVA)**
**Badge:** 🟢 PVA  
**Trust Level:** High  

Requirements:
- External AI generator confirms metadata  
- API call returns prompt, model, timestamps  
- Optional cryptographic signing (future version)  

Intended for:
- Suno Verified Tracks  
- Veo Verified Videos  
- SDXL / Runway Verified Images  
- Enterprise or legal-sensitive applications  

#### Manifest Fields Required:
"verification": {
"trust_level": "platform-verified",
"method": "platform-api",
"verified_email": true,
"platform_api": "suno | veo | runway | sdxl | other",
"signature": "base64-digital-signature"
}

---

## 3. Verification Metadata Schema

All AIFF (AI Format Foundation) formats MUST include:
"verification_notes": "",
"reviewed_by": "",
"verification_version": "1.0"

---

## 4. Verification Workflow

### 🟡 Self-Declared Workflow
1. Creator fills metadata  
2. Converter wraps file  
3. Manifest is stored as-is  
4. Badge = SDA  

### 🔵 Verified Creator Workflow
1. Creator logs in  
2. Email verification sent  
3. Creator signs authorship statement  
4. Application hashes signature  
5. Manifest updated  
6. Badge = VC  

### 🟢 Platform Verified Workflow
1. Creator provides AI platform track/video/image ID  
2. Converter calls API:  
GET /metadata/{id}
3. Metadata validated  
4. Optional digital signature verified  
5. Manifest updated  
6. Badge = PVA  

---

## 5. Badge Display Rules

### 🟡 SDA  
Displayed anywhere the file appears.  
Lower priority in rankings and discovery.

### 🔵 VC  
Displayed with creator profile and content cards.  
Eligible for monetization and promotion.

### 🟢 PVA  
Displayed prominently.  
Mark of highest authenticity.  
Eligible for premium-tier placement and enterprise use.

---

## 6. Security & Anti-Fraud Considerations

- Manifest fields must be immutable after signing  
- Hash-based signatures prevent metadata tampering  
- Optional blockchain anchoring may be supported in future versions  
- API-level verification prevents fraudulent metadata  
- Converter tools MUST log verification decisions  

---

## 7. Future Extensions (Version 2.0 Roadmap)

- Digital certificate signing for `.aim` / `.aiv` / `.aii` / `.aip`  
- Public key directory for platforms  
- Blockchain metadata anchoring  
- Verification revocation system  
- Partnered verification nodes  
- Federation across multiple creative tools  

---

## 8. Compliance Statement

Implementations that fully adhere to this spec may display:

AI Format Foundation
Verification Compliance Mark (VCM)
Version 1.0

Non-compliant tools must NOT use the verification badges or claim alignment.

---

## 9. Changelog

**1.0 – Initial Release**
- Establishes SDA, VC, PVA tiers  
- Introduces manifest verification schema  
- Defines badge behavior  
- Outlines workflow requirements  
- Includes future-ready API verification system  
