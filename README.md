# Introduction to cryptography - the Vigenère cipher
In [my first cryptography blogpost](https://github.com/yo-yo-yo-jbo/crypto_terminology/) I introduced some definitions and concepts, one of them was the concept of `substitution ciphers`. In short, those ciphers substitute plaintext tokens by some methodology that depends on the cipher's `key`. I did forget to mention - encryption and decryption methodologies might be slightly different but the key would be used for both encryption and decryption - those ciphers are known as `symmetric ciphers`.  
We've seen examples of `monoalphabetic substitution ciphers` - those are ciphers that substitute *one letter* each time. We've also seen how one can use `frequency analysis` to break the cipher.  

In this blogpost, I'd like to show an example of a non-monoalphabetic substitution cipher, explain why naive frequency analysis fails on it and how one might still attempt to break the cipher.  
Armed with the knowledge of modular arithmetics from [my previous blogpost](https://github.com/yo-yo-yo-jbo/crypto_modular/), this should be a breeze!

## Motivation
We've seen that monoalphabetic ciphers are vulnerable to frequqncy analysis since the same letter in plaintext is encrypted to the letter in ciphertext.  
You could create a naive yet more complex substitution ciphers - for example, having each two letters mapped to other two letters. Those are called `digraphs` and a well-known example of a digraph is the [Playfair Cipher](https://en.wikipedia.org/wiki/Playfair_cipher). The security of such ciphers is much better than monoalphabetic substitution ciphers, but it's still vulnerable to some frequency analysis (e.g. `th` in English is way more common than `zx`). There are other, more sophisticated techniques to crack Playfair - I won't discuss them here.  
The big advantage of `Playfair` (and other `digraph ciphers`) is that the distribution in the ciphertext is much more uniform, so more text is required for a serious frequency analysis. You could go beyond that (do something similar for 3-letters, 4-letters and so on) but similar claims could be made - sufficient ciphertext enables frequency analysis.  

## The cipher
The Vigenère cipher does something novel - instead of encrypting by a constant `n-gram` (3-letters etc.) it encrypts each letter with a letter from a different alphabet, derived by the encryption key. We could therefore classify that cipher as a `polyalphabetic substitution cipher` with a frequency that depends on the key length - which makes naive frequency analysis impractical.  
Let's see an example. For that we will be using a `Tabula Recta` (also known as a `Vigenère square`, which is pretty self-explanatory:
![Tabula Recta](tabula.png)
