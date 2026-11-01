# 🔐 File Encryption and Decryption

A Java-based desktop application for securely encrypting and decrypting files using **AES-128-GCM authenticated encryption**. It features a simple graphical interface built with Java Swing and password-based key derivation using PBKDF2-HMAC-SHA256.

## 📌 Overview

FileEncryptGUI allows users to encrypt files with a password and decrypt them when needed. Each encryption operation generates a random salt and initialization vector (IV), while GCM authentication helps detect unauthorised modifications to encrypted data.

The application is designed to demonstrate practical file security, cryptographic techniques and GUI-based application development in Java.

## ✨ Features

- **File Selection:** Browse and select files through a graphical file picker.
- **Secure Encryption:** Encrypt files using AES-128-GCM.
- **Password-Based Security:** Derive encryption keys using PBKDF2-HMAC-SHA256.
- **Record ID Management:** Assign unique IDs to encrypted files.
- **Decrypt by ID:** Retrieve and decrypt files using their Record IDs.
- **Direct File Decryption:** Select and decrypt `.enc` files without requiring a stored Record ID.
- **Tamper Detection:** GCM authentication detects modifications to encrypted data.
- **Operation Logs:** View encryption and decryption results in the application.

## 🛠️ Technologies Used

| Technology | Purpose |
|---|---|
| Java 11+ | Core programming language |
| Java Swing | Graphical user interface |
| Java Cryptography Architecture (JCA) | Cryptographic operations |
| AES-128-GCM | Authenticated file encryption |
| PBKDF2-HMAC-SHA256 | Password-based key derivation |

**Dependencies:** No external libraries or build tools required.

## 🔒 Cryptographic Details

| Parameter | Configuration |
|---|---|
| Encryption Algorithm | AES-128-GCM |
| Key Derivation | PBKDF2-HMAC-SHA256 |
| PBKDF2 Iterations | 100,000 |
| Salt Length | 16 bytes |
| IV / Nonce Length | 12 bytes |
| Authentication Tag | 128 bits |

### Encrypted File Format

Each encrypted file follows this binary structure:

```text
+------------------------+
| Salt (16 bytes)        |
+------------------------+
| IV / Nonce (12 bytes)  |
+------------------------+
| Ciphertext + GCM Tag   |
+------------------------+
```

The random salt and IV are generated for each encryption operation. During decryption, the application derives the key again from the supplied password and verifies the authentication tag.

## ⚙️ Requirements

- Java Development Kit (JDK) 11 or later.
- Any operating system supporting Java Swing.
- No external dependencies.

## 🚀 Getting Started

### 1. Clone the Repository

```bash
git clone https://github.com/bhaa1403thi/File-Encryption-and-Decryption.git
```

### 2. Navigate to the Project Directory

```bash
cd File-Encryption-and-Decryption
```

### 3. Compile the Application

```bash
javac FileEncryptGUI.java
```

### 4. Run the Application

```bash
java FileEncryptGUI
```

## 📖 How to Use

1. Launch the application.
2. Click **Browse** and select the file you want to encrypt.
3. Enter a unique Record ID and a strong password.
4. Click **Encrypt** to generate an encrypted `.enc` file.
5. To decrypt, enter the same Record ID and password, then select **Decrypt by ID**.
6. Alternatively, select **Decrypt from file** to choose an encrypted `.enc` file directly.
7. Use **List Records** to view the encrypted file mappings available during the current session.

The application displays operation results and error messages in its log area.

## 📁 Project Structure

```text
File-Encryption-and-Decryption/
│
├── FileEncryptGUI.java
│   ├── CryptoEngine
│   ├── AesGcmCryptoEngine
│   └── FileEncryptGUI
│
└── README.md
```

- **CryptoEngine:** Defines the encryption and decryption contract.
- **AesGcmCryptoEngine:** Implements AES-GCM encryption and decryption with PBKDF2-based key derivation.
- **FileEncryptGUI:** Provides the Java Swing interface and handles user interactions.

## ⚠️ Important Notes

- Record ID mappings are stored in memory and are lost when the application closes.
- Encrypted `.enc` files are not automatically deleted when the application closes.
- Keep your passwords safe. Losing the password makes decryption impossible.
- Decrypted files are saved with a `.bin` extension and can be renamed if necessary.
- Use a strong, unique password for better security.

## 🔮 Future Improvements

- Persistent encrypted file record management.
- Support for custom output locations and filenames.
- Improved password strength validation.
- Enhanced user interface and file management.
- Additional security and usability improvements.

## 📜 License

This project is licensed under the **MIT License**. See the `LICENSE` file for details.
