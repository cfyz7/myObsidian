apt install wireguard

wg genkey | tee /etc/wireguard/private.key | wg pubkey > 
/etc/wireguard/public.key

Start WireGuard
sudo systemctl start wg-quick@client

Откройте терминал в Ubuntu и используйте следующую команду, чтобы остановить службу WireGuard: sudo systemctl stop wg-quick@wg0.service

Чтобы отключить службу WireGuard VPN в Ubuntu, используйте следующую команду: sudo systemctl disable wg-quick@wg0.service

Это предотвратит автоматический запуск службы WireGuard при запуске системы.

Вы также можете проверить статус службы WireGuard с помощью следующей команды: sudo systemctl status wg-quick@wg0.service
Если служба остановлена, она будет отображаться как неактивная или мертвая.