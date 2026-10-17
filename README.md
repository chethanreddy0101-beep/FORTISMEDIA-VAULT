# FORTISMEDIA-VAULT
# CipherMedia

CipherMedia is a simple web application for password-based encryption and decryption of image, audio, and video files. It uses AES-256-GCM for authenticated encryption and scrypt to derive a cryptographic key from a password.

## Features

- Encrypt supported image, audio, and video files.
- Decrypt files created by CipherMedia (`.cmenc`).
- Use your own password or generate a strong random key automatically.
- Detect incorrect passwords and modified or damaged encrypted files.
- Drag and drop files into the upload area.
- Download the processed file directly from the browser.
- Process files in memory; the application does not intentionally save uploaded files to disk.
- Maximum upload size: 200 MB.
- No login or registration required.

## Technologies Used

- **Frontend:** HTML, CSS, JavaScript
- **Backend:** Python, Flask
- **Cryptography:** `cryptography` library, AES-256-GCM, scrypt

## Supported File Types

CipherMedia accepts these file extensions for encryption:

- **Images:** `.jpg`, `.jpeg`, `.png`, `.gif`, `.webp`, `.bmp`, `.tiff`, `.svg`, `.heic`, `.avif`
- **Audio:** `.mp3`, `.wav`, `.flac`, `.aac`, `.ogg`, `.m4a`, `.opus`
- **Video:** `.mp4`, `.mov`, `.mkv`, `.webm`, `.avi`, `.m4v`, `.mpeg`, `.mpg`

Encrypted files use the `.cmenc` extension.

## Project Structure

Arrange the files in the following structure so Flask can find the HTML template and static assets:

```text
CipherMedia/
├── app.py
├── requirements.txt
├── templates/
│   └── index.html
└── static/
    ├── app.js
    └── style.css
```

If your files are currently in one folder, move `index.html` into `templates/` and move `app.js` and `style.css` into `static/`.

## Requirements

- Python 3.10 or later recommended
- pip
- A modern web browser

## Installation and Setup

### 1. Clone the repository

```bash
git clone <YOUR_GITHUB_REPOSITORY_URL>
cd CipherMedia
```

Replace `<YOUR_GITHUB_REPOSITORY_URL>` with the URL of your GitHub repository.

### 2. Create a virtual environment (recommended)

**Windows:**

```powershell
python -m venv .venv
.venv\Scripts\activate
```

**macOS/Linux:**

```bash
python3 -m venv .venv
source .venv/bin/activate
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

The `requirements.txt` file includes Flask and the `cryptography` library.

### 4. Run the application

```bash
python app.py
```

Open the local address shown by Flask in your browser. By default, Flask uses:

```text
http://127.0.0.1:5000
```

## How to Use

### Encrypt a file

1. Open CipherMedia in your browser.
2. Select **Encrypt**.
3. Choose **My password** and enter a password of at least 8 characters, or select the automatic key option.
4. Select or drag and drop a supported media file.
5. Click **Encrypt file**.
6. Download the `.cmenc` file.
7. If you used an automatically generated key, copy and save it securely immediately. It is shown only once.

### Decrypt a file

1. Select **Decrypt**.
2. Choose the `.cmenc` file created by CipherMedia.
3. Enter the same password or generated key used during encryption.
4. Click **Decrypt file**.
5. Download the restored original file.

## Security Notes

- AES-256-GCM provides encryption and authentication. It helps detect tampering and incorrect passwords.
- scrypt derives a 256-bit key from the supplied password using a random salt.
- A random nonce and salt are generated for each encryption operation.
- The original filename is stored inside the encrypted payload and is protected by encryption.
- The application processes uploads in memory and does not intentionally store them on the server. However, uploaded data is transmitted to the server, so only use a server you trust.
- **Keep your password or generated key safe.** There is no password or key recovery feature. If it is lost, the encrypted file cannot be decrypted.
- Use a strong, unique password. A password with at least 8 characters is required by the application; a longer passphrase is recommended.

## Limitations

- Maximum file size is 200 MB.
- Only the listed media file extensions are accepted for encryption.
- Decryption is intended for `.cmenc` files produced by CipherMedia.
- The app has no user accounts, database, or password recovery feature.
- This project is provided as a learning/minor-project application and has not been presented as a professionally audited security product.

## Troubleshooting

**The page does not open**
- Confirm that the virtual environment is activated, dependencies are installed, and `python app.py` is running.
- Open `http://127.0.0.1:5000` in your browser.

**The app says the password is wrong or the file is damaged**
- Check that you entered the same password or generated key used during encryption.
- Make sure the `.cmenc` file has not been changed or corrupted.

**The generated key is lost**
- CipherMedia cannot recover it. You will need the original key to decrypt the file.

**A file is rejected**
- Check that its extension is supported and that it is not empty or larger than 200 MB.

## License

No license has been specified yet. Add a `LICENSE` file before distributing the project if you want to define reuse and redistribution permissions.
