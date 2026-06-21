# AI File Organizer – Android

Aplikasi Android **merapikan file SD Card / internal storage pakai AI Gemini**, 100% SAF Scoped Storage, tidak pernah menyentuh file sistem.

- Target: Android 11+ / API 30+, compileSdk 34
- AI: Google Gemini 1.5 Flash
- OCR on-device: ML Kit Text Recognition
- PDF parse: PDFBox-Android
- UI: Jetpack Compose Material3

## Fitur
- Pilih folder via `ACTION_OPEN_DOCUMENT_TREE` – app HANYA akses folder itu.
- Blacklist otomatis: `/Android`, `/Android/data`, `/Android/obb`, `.android_secure`, `MIUI`, `LOST.DIR`
- Full Content Analysis:
  - TXT/MD/CSV/JSON → baca langsung
  - PDF → extract 2 halaman pertama
  - Gambar → OCR ML Kit (struk Tokopedia/Shopee, screenshot, KTP)
- Gemini batch 12 file → kategori + rename rapi
- Preview Plan → Dry-Run → Eksekusi
- API Key disimpan EncryptedSharedPreferences

Kategori:
`Dokumen_Kerja, Dokumen_Pribadi, Struk_Invoice, Foto_Pribadi, Foto_Keluarga, Screenshot, Video, Audio_Musik, Ebook, Arsip_Project, APK_Installer, Download_Random, Lainnya`

Output: `[FolderPilihan]/AI_Organized/[Kategori]/[Sub]/`

## Build Lokal
1. Android Studio Hedgehog+
2. Open folder
3. Sync Gradle
4. Run / Build APK

API Key gratis: https://aistudio.google.com/app/apikey

## Build via GitHub Actions
1. Buat repo baru di GitHub
2. Push project ini
3. Actions > Android CI akan build otomatis
4. Download APK di Artifacts / Releases

```
git init
git add .
git commit -m "AI File Organizer v1"
git branch -M main
git remote add origin https://github.com/USERNAME/ai-file-organizer.git
git push -u origin main
```

APK debug & release muncul di: Actions → Artifacts.

## Struktur
```
app/src/main/java/com/arena/aifileorganizer/
 MainActivity.kt
 OrganizerViewModel.kt
 data/ApiKeyStore.kt
 data/GeminiClient.kt
 organizer/FileScanner.kt
 organizer/ContentExtractor.kt
 organizer/AiCategorizer.kt
 organizer/FileMover.kt
 model/Models.kt
 ui/...
```

MIT License
