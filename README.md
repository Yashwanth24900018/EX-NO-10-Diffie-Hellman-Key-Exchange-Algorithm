# EX-NO-10-Diffie-Hellman-Key-Exchange-Algorithm

## AIM:
To Implement Diffie Hellman Key Exchange Algorithm 

## Algorithm:

1. Diffie-Hellman Key Exchange is used for securely sharing a secret key between two parties over an insecure channel.

2. Initialization: Agree on a large prime number \( p \) and a primitive root \( g \) modulo \( p \) (both are public values).

3. Key Exchange Process: 
   - Each party selects a private key and calculates their public key using the formula \( g^{\text{private key}} \mod p \).
   - Each party then shares their public key with the other.

4. Secret Key Computation: 
   - Each party computes the shared secret key using the received public key and their own private key.

5. Security: The difficulty of computing discrete logarithms ensures that the shared key remains secure even if public values are intercepted.

## Program:
```
#include <stdio.h>

// Function for modular exponentiation
long long modExp(long long base, long long exp, long long mod) {
    long long result = 1;
    while (exp > 0) {
        if (exp % 2 == 1)
            result = (result * base) % mod;
        base = (base * base) % mod;
        exp /= 2;
    }
    return result;
}

int main() {
    long long p = 23;   // Public prime number
    long long g = 5;    // Primitive root of p

    long long a, b;     // Private keys
    long long A, B;     // Public keys
    long long key1, key2;

    printf("Enter private key for User A: ");
    scanf("%lld", &a);

    printf("Enter private key for User B: ");
    scanf("%lld", &b);

    // Generate public keys
    A = modExp(g, a, p);
    B = modExp(g, b, p);

    // Generate shared secret keys
    key1 = modExp(B, a, p);  // Key computed by User A
    key2 = modExp(A, b, p);  // Key computed by User B

    printf("\nPublic Parameters:");
    printf("\np = %lld, g = %lld", p, g);

    printf("\n\nPublic Keys:");
    printf("\nUser A public key: %lld", A);
    printf("\nUser B public key: %lld", B);

    printf("\n\nShared Secret Keys:");
    printf("\nKey computed by User A: %lld", key1);
    printf("\nKey computed by User B: %lld\n", key2);

    return 0;
}
```


## Output:

[Screenshot 2026-02-26 205324.pdf](https://github.com/user-attachments/files/25579803/Screenshot.2026-02-26.205324.pdf)


## Result:

The program is executed successfully

