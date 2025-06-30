
## Documentation

This section provides instructions for generating a secure Argon2 hash with a random salt, suitable for use in Vaultwarden deployments.

### Hash Generation

To generate a secure hash for your password:

1. Use a strong password as input.
2. Generate a random salt using `openssl`.
3. Hash the password with Argon2 using the generated salt.

The provided command demonstrates how to pipe your password into Argon2, using a randomly generated salt, and outputs the hash in a format compatible with Vaultwarden.

**Note:**  
- The example output shows the typical format of an Argon2 hash.
- Replace `"MySecretPassword"` with your actual password.
- Adjust Argon2 parameters (`-k`, `-t`, `-p`) as needed for your security requirements.

```sh
❯ echo -n "MySecretPassword" | argon2 "$(openssl rand -base64 32)" -e -id -k 65540 -t 3 -p 4
$argon2id$v=19$m=65540,t=3,p=4$OUVpYnk3TFFxeUdoQ3BuV3Y3aVk3MlQvbHp4ZXJzTHNBM2p5SEFJOGhJZz0$/8BAaK/6V1AeB9HeE4h9gCsGAcbuCrVT0dexlnmpIEs
``` 

#### Usage in Docker Compose

When using this hash in a `docker-compose.yml` file, escape environment variable references with double dollar signs (`$$`). This ensures Docker Compose evaluates variables at container startup, not during YAML parsing or shell execution.

#### Accessing the Admin Panel

After deployment, access the Vaultwarden admin panel at: [http://localhost:8000/admin](http://localhost:8000/admin)
