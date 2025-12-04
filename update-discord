#!/bin/bash

# URL for the latest Discord .deb
DISCORD_URL="https://discord.com/api/download/stable?platform=linux&format=deb"

DOWNLOAD_DIR="/tmp"

# Download the latest version
wget -O "$DOWNLOAD_DIR/discord_latest.deb" "$DISCORD_URL"

# Get the version of the downloaded package
NEW_VERSION=$(dpkg-deb -f "$DOWNLOAD_DIR/discord_latest.deb" Version)

# Get the currently installed version
CURRENT_VERSION=$(dpkg-query -W -f='${Version}' discord 2>/dev/null)

if [ "$NEW_VERSION" != "$CURRENT_VERSION" ]; then
    echo "New version available. Installing..."
    sudo apt install "$DOWNLOAD_DIR/discord_latest.deb"
else
    echo "Discord is up to date."
fi

# Clean
rm "$DOWNLOAD_DIR/discord_latest.deb"
