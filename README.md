# IP Checker Service

Simple service that returns the public IP of whoever connects to it.

## Setup

1. **Deploy files**:

   ```bash
   sudo mkdir -p /var/www/ip.jamon.dev
   sudo cp index.html /var/www/ip.jamon.dev/
   ```

2. **Configure nginx**:

   - Copy `nginx.conf` to `/etc/nginx/sites-available/ip.jamon.dev`
   - Create symlink: `sudo ln -s /etc/nginx/sites-available/ip.jamon.dev /etc/nginx/sites-enabled/`
   - **If `ip.jamon.dev` exists in `/etc/nginx/sites-available/default`**, remove it to avoid conflicts:
     ```bash
     sudo nano /etc/nginx/sites-available/default
     # Remove or comment out the server block for ip.jamon.dev
     ```
   - Test config: `sudo nginx -t`
   - Reload nginx: `sudo systemctl reload nginx`

3. **SSL**:
   - If SSL certificates already exist (from Certbot), the config includes them automatically
   - If not, run: `sudo certbot --nginx -d ip.jamon.dev`

That's it! No scripts or additional services needed.
