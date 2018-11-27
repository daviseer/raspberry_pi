# raspberry_pi
projects developed to Raspberry Pi 

// author Davi Seer

>>> Autostart browser on raspberry pi <<< ,
(Language: Portuguese - BR)

>>Iniciar browser ao iniciar raspberry pi

(foi seguido os passos indicados neste endereço: https://www.raspberrypi.org/forums/viewtopic.php?t=171318)

Testado com autologin para o usuário pi
Abra o terminal e siga estas instruções:

Crie um diretório bin para o usuario:
$ mkdir -p /home/pi/bin

Edite um arquivo “kiosk.sh” nesse diretório: 
$ nano /home/pi/bin/kiosk.sh

Digite esse conteúdo:

#!/bin/bash
export DISPLAY=:0.0
xset s off
xset -dpms
xset s noblank
sleep 15
chromium-browser->(aqui vai o programa a ser iniciado) --noerrdialogs --disable-session-crashed-bubble --disable-infobars –ignore-certificate-errors --kiosk OU -start-fullscreen http://google.com https://191.36.57.254:3000/ https://191.36.57.254:441 http://agendamento.garopaba.ifsc.edu.br/day.php?year=2018&month=6&day=12&area=2&room=32 http://191.36.57.245/screens.php?elementid=20&fullscreen=1 <<-(DIGITE AQUI O ENDEREÇO DA PAGINA À SER ABERTA JUNTO AO BROWSER)

Mude a permissão do arquivo: 
$ sudo chmod 755 /home/pi/bin/kiosk.sh

(Crie um novo diretório, se ele não existir: ) 
$ sudo mkdir -p /home/pi/.config/autostart/

Crie um arquivo novo: 
$ sudo nano /home/pi/.config/autostart/kiosk.desktop

Digite e salve (ctrl+x, y, start):
[Desktop Entry]
Type=Application
Name=Kiosk
Comment=
Exec=/home/pi/bin/kioww{{sk.sh
Terminal=false
Hidden=false

Agora o raspberry pi, ao iniciar junto ao usuário pi, abrirá o navegador automaticamente um modo kiosk

>>Salvando abas abertas no chrome sem reiniciar histórico:
Abra o navegador (no caso utilizamos o Chromium)
Deixe aberto as abas desejadas para iniciarem automaticamente ao iniciar
Abra o terminal (Ctrl+Alt+T)
digite: cd ./config/chromium/Default 
agora, faça uma cópia de segurança para estes arquivos(pois iremos modifica-los):
$ sudo cp Preferences Preferences_original
$ sudo cp History History_original

$ sudo nano Preferences
Procure pelo arquivo exit_type: Ctrl+W exit_type
Mude para “exit_type”:”Normal”
Feche e salve: Ctrl+X, y, enter
Agora, modificaremos a permição do arquivo Preferences:
$ sudo chattr +i Preferences 

>>backup : https://www.raspberrypi.org/documentation/linux/filesystem/backup.md
Aqui estão algumas instruções sobre o backup com RaspberryPi no Linux.

https://maker.pro/raspberry-pi/tutorial/how-to-back-up-your-raspberry-pi-project-files



