# EX-NO-13-MESSAGE-AUTHENTICATION-CODE-MAC

## AIM:
To implement MESSAGE AUTHENTICATION CODE(MAC)

## ALGORITHM:

STEP-1: Message Authentication Code (MAC) is a cryptographic technique used to verify the integrity and authenticity of a message using a secret key.

STEP-2: Initialization
Select a cryptographic hash function (H) such as SHA-256 and a secret secret key (K). The message (M) to be authenticated is taken as input along with the key.

STEP-3: MAC Generation
Compute the MAC by applying the hash function to the combination of the secret key and the message:
MAC(M, K) = H(K || M), where || denotes concatenation of K and M.

STEP-4: Verification
The receiver, who knows the same secret key (K), recomputes the MAC using the received message (M) and the hash function, and generates a new MAC value.

STEP-5: Comparison and Security
The computed MAC is compared with the received MAC. If both match, the message is authentic and unchanged. If not, it is tampered. The security depends on the secrecy of key (K) and strength of hash function (H).

## Program:

```
#include <stdio.h>
#include <string.h>

void generateMAC(char msg[], char key[], char mac[])
{
    int i;
    for(i = 0; msg[i] != '\0'; i++)
    {
        mac[i] = msg[i] ^ key[i % strlen(key)];
    }
    mac[i] = '\0';
}

int main()
{
    char msg[100], key[100], mac[100];
    printf("Enter message: ");
    scanf(" %[^\n]", msg);
    printf("Enter key: ");
    scanf(" %[^\n]", key);
    msg[strcspn(msg, "\n")] = '\0';
    key[strcspn(key, "\n")] = '\0';
    generateMAC(msg, key, mac);
    printf("\nGenerated MAC: %s\n", mac);
    return 0;
}
```

## Output:

<img width="1913" height="899" alt="ex13op" src="https://github.com/user-attachments/assets/7f229c7a-9e50-4f27-bd95-85a2edf4a55b" />

## Result:
Thus, the implementation of Message Authentication Code (MAC) had been executed successfully.
