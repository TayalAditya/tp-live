fi

# Root-owned pieces: the timer, the service and the NetworkManager hook, which
# NetworkManager only runs when the file is owned by root and not writable by
# anyone else.
sudo_run install -m 0644 -o root -g root "$HERE/tp-live-link.service" /etc/systemd/system/tp-live-link.service
sudo_run install -m 0644 -o root -g root "$HERE/tp-live-link.timer" /etc/systemd/system/tp-live-link.timer
sudo_run install -m 0755 -o root -g root "$HERE/91-tp-live" /etc/NetworkManager/dispatcher.d/91-tp-live
sudo_run systemctl daemon-reload
sudo_run systemctl enable -q --now tp-live-link.timer

echo
echo "Installed. Deploy key to add to $REPO (write access):"
cat "$KEY.pub"
echo
