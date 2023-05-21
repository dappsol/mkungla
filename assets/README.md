<h1>Public assets</h1>

**Table of Contents**

- [Importing and verifying the GPG Key](#importing-and-verifying-the-gpg-key)
  - [Install dependencies if they are not already installed:](#install-dependencies-if-they-are-not-already-installed)

---

## Importing and verifying the GPG Key

For signing and encryption I use follwoing GPG Key 

| | |
| --- | --- |
| public key file | [marko@mkungla.dev.gpg](marko@mkungla.dev.gpg) |
| fingerprint | `5752D8551F78CEE4542F5693F2AFEDFD305C790F` |
| long id | `F2AFEDFD305C790F` |
| short id | `305C790F` |


### Install dependencies if they are not already installed:

- **Red Hat/Fedora**

     ```bash
    sudo dnf install gnupg2 curl
    ```

- **Debian/Ubuntu**

    ```bash
    sudo apt update
    sudo apt install gnupg curl
    ```

- **Arch Linux**

    ```bash
    sudo pacman -Sy gnupg curl
    ```

- **macOS**

    If you haven't already, install [GPG Suite](https://gpgtools.org/).

- **Windows**

    If you haven't already, install [Gpg4win](https://gpg4win.org/).


**2. Download and import the GPG key:**

You can either import it from key server or import it manually

- **From key server**

    ```bash
    gpg --recv-keys $(dig +short TXT gpg.fingerprint.mkungla.dev | tr -d '"')
    # or
    gpg --recv-keys 5752D8551F78CEE4542F5693F2AFEDFD305C790F
    ```

**Manual import**

- **Linux and macOS**

    ```bash
    curl https://mkungla.dev/assets/marko@mkungla.dev.gpg | gpg --import
    ```
- **Windows**

    1. Download the key from https://mkungla.dev/assets/marko@mkungla.dev.gpg
    2. Open Kleopatra, which was installed with Gpg4win.
    3. In the "File" menu, select "Import Certificates" and select the downloaded key file to import it.

**3. Verifying the Key**

Once the key is imported, you can verify that the correct key has been imported by checking the key's fingerprint. Here's how you can do that:

- **Linux and macOS**

    ```bash
    gpg --fingerprint marko@mkungla.dev
    ```

    This command should output the key's fingerprint. Verify that the fingerprint matches the fingerprint of the key you intended to import.

    You can also use this key to verify the authenticity of signed files. For example, to verify the signature of the README file:

    1. Download the README file and its signature:

        ```bash
        curl -O https://mkungla.dev/assets/README.md
        curl -O https://mkungla.dev/assets/README.md.asc
        ```
    2. Verify the signature:

        ```bash
        gpg --verify README.md.asc README.md
        ```
    

    If the key is correctly imported and the files have not been tampered with, GPG should output a message indicating that the signature is good and showing the key ID and the signer's email address. If the files have been tampered with, GPG will output a message indicating that the signature is bad.

- **Windows**

    1. Open Kleopatra.
    2. In the main window, you should see the imported key listed. Right-click on the key and select `Details`.
    3. The fingerprint is listed under `Fingerprint`. Verify that the fingerprint matches the fingerprint of the key you intended to import.
    

    *You can also use this key to verify the authenticity of signed files. For example, to verify the signature of the README file:*

    1. Download the README file and its signature from the following URLs:
       - https://mkungla.dev/assets/README.md
       - https://mkungla.dev/assets/README.md.asc
    2. Open Kleopatra.
    3. Click on `Decrypt/Verify` in the toolbar.
    4. In the dialog that appears, navigate to and select the .asc file you downloaded in step 1. Click `Open`.
    5. Kleopatra will verify the signature and show a verification result. If the key is correctly imported and the files have not been tampered with, Kleopatra should indicate that the signature is correct. If the files have been tampered with, Kleopatra will indicate that the signature is bad.







    


