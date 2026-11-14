# NB SmartFit — Render deployment (Bahasa Melayu)

**Ini prototaip tugasan, bukan laman rasmi New Balance.** Harga dan ciri produk ialah data contoh. Tiada checkout/pembayaran sebenar.

## Upload ke GitHub
1. Buka github.com dan log masuk / cipta akaun.
2. Klik **New repository**; nama contoh `nb-smartfit-demo` dan pilih **Private** jika mahu.
3. Cipta repository, kemudian pilih **Add file > Upload files**.
4. **Extract ZIP ini dahulu** dan upload empat fail `index.html`, `server.js`, `package.json`, `README.md` (jangan upload ZIP sahaja). Klik **Commit changes**.
5. Jangan upload fail API key, `.env`, screenshot key, atau masukkan key dalam kod.

## Deploy di Render
1. Pergi ke dashboard.render.com, sign in, pilih **New > Web Service**.
2. Connect akaun GitHub dan pilih repo `nb-smartfit-demo`.
3. Language/Runtime: `Node`.
4. Build Command: `npm install`.
5. Start Command: `npm start` (atau `node server.js`).
6. Pilih Free jika tersedia dan sesuai (periksa had pelan semasa).
7. Di **Environment**, tambah `OPENAI_API_KEY` dengan nilai key sebenar. Simpan sebagai secret/private environment variable. Jika tidak diset semasa awal setup, pergi ke Environment selepas buat servis dan redeploy.
8. Klik **Deploy Web Service**. Tunggu status **Live** dan buka pautan `https://<nama>.onrender.com` yang Render beri.
9. Uji `https://<nama>.onrender.com/api/status` untuk `configured:true`, kemudian test chatbot secara sebenar. `configured:true` bermaksud key tersedia; ia bukan jaminan kredit API mencukupi.

**Keselamatan/kos:** Tetapkan usage limits dan bajet di OpenAI Platform. Web service awam boleh mengakibatkan caj API daripada pelawat. Rate limiter terbina dalam ialah perlindungan asas sahaja (per-IP dan dalam memori), bukan kawalan kos menyeluruh. Untuk dikongsi luas, tambah pengesahan akses / hard cap di server.

## Run secara local
```powershell
$env:OPENAI_API_KEY="YOUR_SECRET_KEY"
npm start
```
Buka http://127.0.0.1:3000 (localhost kini melalui 0.0.0.0; jangan dedahkan port kepada internet).