# Jellyfin Deployment Notes

## Default Port

- The default port for the Jellyfin instance is **8096**.

## User and Group IDs for Docker

- To obtain your user ID (UID), run:  
    ```sh
    id -u
    ```
- To obtain your group ID (GID), run:  
    ```sh
    id -g
    ```

## Media Directory Ownership

- Ensure your media directories are owned by the same user and group specified in your `docker-compose.yml`.
- Set ownership recursively with:  
    ```sh
    chown -R <uid>:<gid> /path/to/media
    ```
- Proper ownership is required for Jellyfin to access and manage your media files.