# File-Encryption-and-Decryption

This file encryption and decryption is developed by using python and fernet 

Fernet

Fernet guarantees that a message encrypted using it cannot be manipulated or read without the key. Fernet is an implementation of symmetric (also known as “secret key”) authenticated cryptography. Fernet also has support for implementing key rotation via MultiFernet.

classcryptography.fernet.Fernet(key)[source]
This class provides both encryption and decryption facilities.

from cryptography.fernet import Fernet
key = Fernet.generate_key()
f = Fernet(key)
token = f.encrypt(b"my deep dark secret")
token
b'...'
f.decrypt(token)
b'my deep dark secret'

encrypt(data)
Encrypts data passed. The result of this encryption is known as a “Fernet token” and has strong privacy and authenticity guarantees.

Parameters: data (bytes) – The message you would like to encrypt.

Returns bytes:A secure message that cannot be read or altered without the key. It is URL-safe base64-encoded. This is referred to as a “Fernet token”.

Raises : TypeError – This exception is raised if data is not bytes.

decrypt(token, ttl=None)[source]
Decrypts a Fernet token. If successfully decrypted you will receive the original plaintext as the result, otherwise an exception will be raised. It is safe to use this data immediately as Fernet verifies that the data has not been tampered with prior to returning it.

Parameters : token (bytes or str) – The Fernet token. This is the result of calling encrypt().

ttl (int) – Optionally, the number of seconds old a message may be for it to be valid. If the message is older than ttl seconds (from the time it was originally created) an exception will be raised. If ttl is not provided (or is None), the age of the message is not considered.

Returns bytes : The original plaintext.

Raises : cryptography.fernet.InvalidToken – If the token is in any way invalid, this exception is raised. A token may be invalid for a number of reasons: it is older than the ttl, it is malformed, or it does not have a valid signature.

TypeError – This exception is raised if token is not bytes or str.
