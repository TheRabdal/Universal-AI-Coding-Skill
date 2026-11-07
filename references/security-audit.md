# Security Audit Checklist

## Scope
Lakukan review proporsional. Audit mendalam untuk perubahan auth, permission, data, API, upload, jaringan, dependency, dan konfigurasi. Jangan mengklaim audit menyeluruh jika hanya membaca sebagian kode.

## Checklist
- Authentication: bypass, session, token, password, reset, MFA.
- Authorization: server-side enforcement, IDOR/BOLA, privilege escalation, tenant isolation, ownership, least privilege.
- Input: validation, SQL/NoSQL injection, XSS, command/template/LDAP injection, path traversal, unsafe deserialization.
- Web/API: CSRF, CORS, CSP, clickjacking, SSRF, open redirect, rate limit, mass assignment, payload size.
- Data: secrets, PII, logs, storage, encryption, retention, backup, error leakage.
- Upload: MIME/content/size validation, safe filenames, storage isolation, overwrite and executable risks.
- Supply chain: provenance, dependency health, lockfiles, lifecycle scripts, known vulnerabilities.
- Operations: debug mode, default credentials, exposed admin endpoints, permissive cloud storage and permissions.
- Mobile/Flutter: secure token storage, deep links, WebView, logs, clipboard, screenshots, backup, client-side trust assumptions.

## Findings
Setiap temuan memuat ID, kategori, severity, lokasi, bukti, dampak, prasyarat, rekomendasi, dan status Confirmed/Suspected/Not Reproduced.

Severity: Critical, High, Medium, Low, Informational. Bedakan bukti dari dugaan. Jangan melakukan eksploitasi, destructive testing, atau scan target eksternal tanpa otorisasi eksplisit.
