# Obfuscation

## What is Obfuscation
- To obfuscate a code means making it difficult to understand for the reader.
- It is a common practice in programming used to protect intellectual property such as the source code.
- The main goal of code obfuscation is to make reverse engineering as difficult as possible for the opposing side.

## [How does code obfuscation work?](https://cybersecurity.asee.co/blog/what-is-code-obfuscation/)

- rename methods & parameters names or signatures
- dummy code insertion
- etc.

## Obfuscation & SSL Pinning

- SSL-Pinning can be bypassed. On the rooted device, if the hacker get access to your source code, they will change or manipulate the source code to always return success from the method where we compare the certificate or public key.
- For example, if I’m not mistaken on jailed break device, the hacker can do reverse engineering and they run Frida script  to bypass the SSL-Pinning
- We can prevent it by using `Obfuscation` technique, which will change the name of the methods, properties, parameters name in the signature of the methods after your build has been successful. So when the hacker try to access the source code, and try to manipulate it. The obfuscation will make the source code difficult to understand or identify where the comparison of the certificates or public key happens.

## Conclusion
- We use https over http to secure the communication
- We use ssl-pinning upon https to be sure that we are talking to a right person
- We use obfuscation upon ssl-pinning to make the ssl-pinning difficult to bypass (popular in Android, but iOS)

## Sources

- [How does code obfuscation work?](https://cybersecurity.asee.co/blog/what-is-code-obfuscation/)
