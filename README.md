# SplitKita

> Split bill bareng, gampang & cepet 💸

PWA untuk split bill dengan fitur:
- Buat sesi & tambah anggota
- Catat pengeluaran per orang
- Split rata atau custom per item
- Hitung otomatis siapa bayar ke siapa (debt simplification)
- History tersimpan di Firebase
- Install di HP (PWA)

## Deploy ke GitHub Pages

1. Fork / buat repo baru di GitHub
2. Upload semua file ini ke repo
3. Buka **Settings → Pages → Source: main branch / root**
4. Akses di `https://username.github.io/nama-repo`
5. Di HP: buka URL → menu browser → **"Add to Home Screen"**

## Struktur File

```
index.html    ← App utama
manifest.json ← PWA config
sw.js         ← Service worker (offline)
icon-192.png  ← Icon PWA
icon-512.png  ← Icon PWA
```

## Firebase Rules (Firestore)

Tambahkan rules ini di Firebase Console → Firestore → Rules:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /sessions/{sessionId} {
      allow read, write: if true;
      match /expenses/{expId} {
        allow read, write: if true;
      }
    }
  }
}
```

> ⚠️ Rules di atas open access. Kalau mau private, tambahkan Firebase Auth dulu.
