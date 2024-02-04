# Introduction to cryptography - the Vigenère cipher
In [my first cryptography blogpost](https://github.com/yo-yo-yo-jbo/crypto_terminology/) I introduced some definitions and concepts, one of them was the concept of `substitution ciphers`. In short, those ciphers substitute plaintext tokens by some methodology that depends on the cipher's `key`. I did forget to mention - encryption and decryption methodologies might be slightly different but the key would be used for both encryption and decryption - those ciphers are known as `symmetric ciphers`.  
We've seen examples of `monoalphabetic substitution ciphers` - those are ciphers that substitute *one letter* each time. We've also seen how one can use `frequency analysis` to break the cipher.  

In this blogpost, I'd like to show an example of a non-monoalphabetic substitution cipher, explain why naive frequency analysis fails on it and how one might still attempt to break the cipher.  
Armed with the knowledge of modular arithmetics from [my previous blogpost](https://github.com/yo-yo-yo-jbo/crypto_modular/), this should be a breeze!

