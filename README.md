# UFW Firewall Setup Guide for Ubuntu

This guide walks you through the steps to set up UFW (Uncomplicated Firewall) on a fresh Ubuntu server. It includes opening necessary ports for SSH and Nginx Proxy Manager.

## 1. Install UFW

UFW is usually installed by default on Ubuntu. If it's not, install it with:

```bash
sudo apt-get update
sudo apt-get install ufw
```

## 2. Enable UFW

Before enabling UFW, allow SSH to ensure you don’t get locked out of your server, lol:

```bash
sudo ufw allow 22/tcp
```

Enable UFW:

```bash
sudo ufw enable
```

## 3. Allow SSH

If you haven't already allowed SSH, you can do so with:

```bash
sudo ufw allow 22/tcp
```

This opens port 22 for SSH connections, essential for remote management.

## 4. Allow Ports for Nginx Proxy Manager

Nginx Proxy Manager uses the following ports:

- **80**: HTTP
- **443**: HTTPS
- **81**: Web UI (Admin Panel)
- **3000**: Custom application
- **3001**: Custom application
- **4000**: Custom application
- **4001**: Custom application

Allow these ports with the following commands:

```bash
sudo ufw allow 80/tcp
sudo ufw allow 443/tcp
sudo ufw allow 81/tcp
sudo ufw allow 3000/tcp
sudo ufw allow 3001/tcp
sudo ufw allow 4000/tcp
sudo ufw allow 4001/tcp
```

## 5. Check UFW Status

To confirm that all the necessary ports are open, check the status of UFW:

```bash
sudo ufw status
```

The output should look similar to this:

```bash
Status: active

To                         Action      From
--                         ------      ----
22/tcp                     ALLOW       Anywhere
80/tcp                     ALLOW       Anywhere
443/tcp                    ALLOW       Anywhere
81/tcp                     ALLOW       Anywhere
3000/tcp                   ALLOW       Anywhere
3001/tcp                   ALLOW       Anywhere
4000/tcp                   ALLOW       Anywhere
4001/tcp                   ALLOW       Anywhere
22/tcp (v6)                ALLOW       Anywhere (v6)
80/tcp (v6)                ALLOW       Anywhere (v6)
443/tcp (v6)               ALLOW       Anywhere (v6)
81/tcp (v6)                ALLOW       Anywhere (v6)
3000/tcp (v6)              ALLOW       Anywhere (v6)
3001/tcp (v6)              ALLOW       Anywhere (v6)
4000/tcp (v6)              ALLOW       Anywhere (v6)
4001/tcp (v6)              ALLOW       Anywhere (v6)
```

## 6. Optional: Deny All Other Traffic [CAUTION]

> This will deny all incoming connections except those you have explicitly allowed and allow all outgoing connections.

To deny all other traffic by default, use:

```bash
sudo ufw default deny incoming
sudo ufw default allow outgoing
```

This will deny all incoming connections except those you have explicitly allowed and allow all outgoing connections.

## 7. Reload UFW (if necessary)

To apply any changes immediately, reload UFW:

```bash
sudo ufw reload
```

## 8. Disable UFW (when necessary)

To disable UFW, use:

```bash
sudo ufw disable
```

## Summary

Successfully set up UFW on server, allowing SSH and the necessary ports for Nginx Proxy Manager. Your server is now more secure, with the firewall configured to permit only the required traffic.
