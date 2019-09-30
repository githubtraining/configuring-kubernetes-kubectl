## Working With Large Secrets

Large secrets that may contain RSA keys or Certificate Tokens that are too long for the secrets value may be placed in the repository within encrypted files, and then decrypted at runtime within the workflow. An example might be a Key Pair issued by Amazon and stored in a '.pem. file to allow `ssh` and or `Ansible` to authenticate to the AWS server instance.

### Encrpting a file to store in the repository

To encrypt a file for storage within a repository you would employ a utility for encryption and decryption of file data. The `gpg` utility has been chosen for this example. To encrypt the file, you would use the `gpg` command against the file on a command line, on a local file system, or a virtual file system with a powershell on a cloud server. IN our example case we are simply encrypting the file on a local desktop system.

```console
$ gpg -c awskeypair.pem
```

The gpg command will prompt you for a 'passphrase' which is the encryption key that will be needed to decrypt the file contents at runtime in the workflow runner.

<img width="400" alt="Screen Shot 2019-09-23 at 9 50 10 AM" src="https://user-images.githubusercontent.com/43185011/65431840-1bcbc100-dde8-11e9-9bed-c5e07fc4f751.png">

The gpg command will ask you to enter the Passphrase twice to ensure it typed correctly. You must remember this exact phrase for the next step.

### Storing the Encryption Passphrase in the Secrets Vault

Once the Passphrase has been used to encrypt the file contents, you must store just the Passphrase value in the screts vault. You would follow the instructions above under the "Adding a New Secret" heading and name your Passphrase somethin that you will then reference in the Actions workflow runner to decrypt the secret.

The procedure encrypts the file contents, and the Passphrase, so that neither value is visible to the end user in unencypted form.

### Storing the encrypted file within a repository

A simple `git add, git commit, and git push' may be used to store your encrypted file in a repository. You may also use the GitHub web interface and choose to add the file through the 'Upload File' button.

<table>
<tr><td>
<img width="1105" alt="Screen Shot 2019-09-23 at 10 00 31 AM" src="https://user-images.githubusercontent.com/43185011/65432346-060acb80-dde9-11e9-8796-6efed010c2c6.png">
</td></tr>
<tr><td>
You may use the 'Upload files' button on the GitHub web interface to upload an encrypted file from your local system.
</td></tr>
</table>

When the gpg command is used to encrypt a file as stated in the example above, the new encrypted file will be output to the user's present working directory and the ".gpg" extension will be added to the original filename.
