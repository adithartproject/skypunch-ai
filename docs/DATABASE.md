# Database Design

# SkyPunch AI

Version: 1.0

Status: Draft

---

# Tujuan

Dokumen ini menjelaskan struktur database yang digunakan oleh SkyPunch AI.

Target database utama:

- Firebase Firestore

Target masa depan:

- PostgreSQL

---

# Firestore Collections

## users

Menyimpan data pengguna.

Field:

- id
- fullName
- email
- role
- photoUrl
- createdAt
- updatedAt

---

## projects

Menyimpan seluruh project.

Field:

- id
- ownerId
- title
- description
- prompt
- framework
- platform
- status
- createdAt
- updatedAt

Status:

- Draft
- Generating
- Completed
- Failed

---

## generated_files

Semua file hasil AI.

Field:

- id
- projectId
- path
- type
- content
- createdAt

Type:

- dart
- yaml
- json
- markdown
- sql

---

## prompts

Riwayat prompt pengguna.

Field:

- id
- projectId
- prompt
- aiModel
- createdAt

---

## builds

Riwayat build.

Field:

- id
- projectId
- status
- apkUrl
- aabUrl
- log
- startedAt
- finishedAt

Status:

- Waiting
- Building
- Success
- Failed

---

## templates

Template aplikasi.

Field:

- id
- name
- category
- description
- icon
- version

---

## ai_models

Model AI.

Field:

- id
- provider
- model
- active

Contoh:

OpenAI

Gemini

Claude

---

# Relationship

users

↓

projects

↓

generated_files

↓

builds

projects

↓

prompts

---

# Index

projects.ownerId

projects.status

generated_files.projectId

builds.projectId

---

# Security

Semua data project hanya dapat diakses oleh pemiliknya.

Admin memiliki akses penuh.

---

# Backup

Backup Firestore dilakukan setiap hari.

Target penyimpanan:

Cloud Storage.

---

# Future

Versi berikutnya akan mendukung:

- PostgreSQL
- Supabase
- MySQL
- MongoDB.
