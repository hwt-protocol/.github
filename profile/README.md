HWT Hash Web Token
- working token library Hwtr https://jsr.io/@hwt/hwtr-js
- demos https://github.com/hwt-protocol/hwt-demo
- canonical info https://hwtprotocol.com
- [spec](https://github.com/hwt-protocol/hwt-protocol/blob/main/SPEC.md) with [conventions](https://github.com/hwt-protocol/hwt-protocol/blob/main/CONVENTIONS.md) expands on the `authz` field authorization schemas and jurisdiction vocabulary
- format `hwt.signature.key-id.expires.format.payload`
```
// payload-data
{
  "iss": "https://auth.example.com",
  "sub": "user@example.com",
  "authz": { "scheme": "RBAC/1.0.2", "roles": ["member"] }
}
// authz-detail
"authz": [
  { "scheme": "RBAC/1.0.2", "roles": ["editor"] },
  {
    "scheme": "/schemas/data-access/v3",
    "datasets": ["analytics"],
    "jur": "HIPAA/1.0/US;GDPR/2.0/DE,FR,NL;CCPA/1.0/US;LGPD/1.0/BR"
  }
]
// delegation-example
{
  "iss": "https://agent-b.example.com",
  "sub": "svc:agent-b",
  "aud": "https://api.target-service.com",
  "tid": "derived-tok-7c8d",
  "iat": 1743900000,
  "authz": { "scheme": "RBAC/1.0.2", "roles": ["editor"] },
  "del": [
    {
      "iss": "https://auth.example.com",
      "sub": "user:4503599627370495",
      "tid": "root-tok-a1b2"
    },
    {
      "iss": "https://agent-a.example.com",
      "sub": "svc:agent-a",
      "tid": "mid-tok-c3d4"
    }
  ]
}
```
