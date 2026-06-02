# ⚡ @crypto/sha2 — SHA-256 for Zeta

**Port of the Rust `sha2` crate (v0.10.x). Pure Zeta implementation.
Also provides HMAC-SHA256 and HKDF.**

---

## 📦 Package

```
zorbs add @crypto/sha2
```

## 🔧 API

### SHA-256 (One-shot)

```zeta
let digest = Sha256::digest("hello world");
// digest is [u8; 32]
```

### SHA-256 (Incremental)

```zeta
let mut hasher = Sha256::new();
hasher.update("part 1 ");
hasher.update("part 2 ");
let digest = hasher.finalize();
```

### HMAC-SHA256

```zeta
let mac = hmac_sha256(key, "message");
// 32-byte MAC tag
```

### HKDF (RFC 5869)

```zeta
let derived = hkdf(salt, ikm, info, 32);
// 32 bytes of derived key material

// Or step-by-step:
let prk = hkdf_extract(salt, ikm);
let okm = hkdf_expand(&prk, info, 32);
```

## 🔬 Verified Against

| Test Vector | Status |
|---|---|
| SHA-256("abc") | ✅ NIST CAVS |
| SHA-256("") | ✅ FIPS 180-4 |
| SHA-256 incremental | ✅ Verified |
| HMAC-SHA256 RFC 4231 Test 2 | ✅ |
| HKDF RFC 5869 Test 1 | ✅ |

## 📦 What's Inside

The package bundles the following Rust crate equivalents as internal modules:

| Module | Source |
|---|---|
| `Sha256` | sha2 v0.10.x — SHA-256 |
| `hmac_sha256()` | hmac v0.12.x — HMAC |
| `hkdf()` | hkdf v0.12.x — HKDF |
| `Digest` | digest v0.10.x — digest trait |
| Buffer mgmt | block-buffer / crypto-common |

## 📄 License

MIT OR Apache-2.0
