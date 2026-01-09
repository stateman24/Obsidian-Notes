# **Encoding vs Encryption vs Hashing**

**Created: 2026-01-09:09:59**
**Tags:** #hashing #encoding #encryption #computiation #swe #f-notes 
____
- Encryption is an encoding technique in which message is encoded by using an encryption algorithm 
- Encoding is to transform data into a form that is readable by most of the system or that can be used by any external  process
- Hashing is to convert data into an hash using some hash function which can be any number generated from a string or text.

| **Encryption**                                                                                                                                                     | **Encoding**                                                                    | **Hashing**                                                                                          |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------- | ---------------------------------------------------------------------------------------------------- |
| Encryption is a type of encoding technique where the message is encoded using an encryption algorithm so that only authorized persons can access that information. | Encoding is a technique where the data is transformed from one form to another. | Hashing is a technique where the data is converted to hash using different algorithms present there. |
| Encryption is a technique used for protecting the confidentiality of the data.                                                                                     | Encryption is used for preserving the usability of the data.                    | Hashing is simply used for checking the integrity of the data.                                       |
| Appropriate Keys are used in the Encryption.                                                                                                                       | No Keys are used in Encoding.                                                   | No Keys are used in Hashing.                                                                         |
| Encryption can be reversed back to its original form by using appropriate keys.                                                                                    | Encoding can be reversed back to its original form.                             | The hashed one cannot be reversed back to its original form.                                         |
| **Example:** AES Algorithm, RSA Algorithm, Diffie Hellman                                                                                                          | **Example:** BASE64, UNICODE, ASCII, URL Encoding.                              | **Example:** MD5, SHA256, SHA - 3.                                                                   |

____
## References
1. https://www.geeksforgeeks.org/dsa/encryption-encoding-hashing/
2. https://medium.com/swlh/the-difference-between-encoding-encryption-and-hashing-878c606a7aff