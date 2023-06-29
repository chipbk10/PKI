# How Digital Signatures work under the hood?

## Digital Signature

- A digital signature employs cryptography to provide two main information security capabilities:
  - **Authentication**: confirming the identity of an individual or organization who signed the data
  - **Integrity**: confirming that the data has not been altered since it was signed
  - **Non-Repudiation**: with digital signature, the sender cannot deny having sent the message later on
 
## Under the hood

- The sender wants to send a document with his digital signature to a receiver
- The sender will pass the document to a [hash]() function to generate a [digest]()
- The sender uses his private key to encrypt the digest (digitial signature - a signed hash)
- The sender sends the document + encrypted digest + [certificate]()
- The receiver checks if the certificate is issued by a trusted CA
- The receiver uses the public key in the certificate to decrypt the encrypted digest
- If the decryption fails, then the document is not sent from the sender
- The receiver uses the same [hash]() algorithm to hash the document and generate a digest
- The receiver compares the generated digest with the decrypted digest
- If they doesn't match, then the document has been tampered on the way

## Application

- 

## Sources

- [How Digital Signatures work under the hood?]([https://blog.adobe.com/en/publish/2016/11/18/how-digital-signatures-work-under-the-hood](https://www.youtube.com/watch?v=TmA2QWSLSPg&ab_channel=SunnyClassroom))
- [How to sign a PDF file in Adobe Reader](https://www.youtube.com/watch?v=GWfo8NlIiKE&ab_channel=AdobeSystemsFederal)
