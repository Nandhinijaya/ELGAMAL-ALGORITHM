# EXP- 12 ELGAMAL-ALGORITHM
# Aim:
To implement the ElGamal cryptosystem for encryption and
decryption.

## Algorithm Steps:
1. Choose a large prime number p and a generator g.
2. Generate the private key and compute the public key.
3. Use the recipient’s public key to encrypt the message.
4. Decrypt the message using the private key.

# Program:
```
#include <stdio.h>
#include <math.h>

int mod_exp(int base, int exp, int mod) {
    int result = 1;
    base = base % mod;
    while (exp > 0) {
        if (exp % 2 == 1)
            result = (result * base) % mod;
        exp = exp >> 1;
        base = (base * base) % mod;
    }
    return result;
}

int main() {
    printf("Experiment 12 - ElGamal Cryptosystem\n");
    printf("Developed by: Nandhini E 212222100030\n");

    int p = 23;
    int g = 5;
    int private_key = 6;
    int public_key = mod_exp(g, private_key, p);

    int plaintext = 8;
    int random_k = 10;
    int c1 = mod_exp(g, random_k, p);
    int c2 = (plaintext * mod_exp(public_key, random_k, p)) % p;

    int decrypted = (c2 * mod_exp(c1, p - 1 - private_key, p)) % p;

    printf("Prime (p): %d\n", p);
    printf("Generator (g): %d\n", g);
    printf("Private Key: %d\n", private_key);
    printf("Public Key: %d\n", public_key);
    printf("Plaintext: %d\n", plaintext);
    printf("Random k: %d\n", random_k);
    printf("Encrypted: (c1 = %d, c2 = %d)\n", c1, c2);
    printf("Decrypted: %d\n", decrypted);

    return 0;
}

```
# Output:
![image](https://github.com/user-attachments/assets/de3d800e-fd97-4779-9d83-5b00a47739df)
# Result:
The plaintext message is successfully encrypted and decrypted
using the ElGamal cryptosystem.
