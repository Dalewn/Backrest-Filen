# Backrest-Filen
Sample compose of Backrest using Filen as backend

## Filen container
This is the default Filen docker container including the CLI version.
On startup it tries to login using the provided credentials and starts a WebDAV server.
This server is accessible only via the internal network _restic-network_

## Backrest container
This is the default Backrest container config with a few additions.
It is also part of the network _restic-network_ and therefore has access to the WebDAV server.
To make use of this, the provided rclone.conf can be used as is.

Alternatively it is possible to log into the container once started and run `rclone config` in order to set up another configuration.
The provided password can only be changed this way since the _rclone.conf_ only stores the password hashed.

# Setup

- Make sure to provide the login credentials to the filen account in the `.env` file.

- Run `docker compose up` to start the stack.

- Within Backrest create a new Repo and use `rclone:filen:restic` as the URI (this expects a folder called _restic_ on top level `\\CloudDrive\restic\`)

- Click __Submit__ and the Repo should be added.