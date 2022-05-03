# Aplicação de Modelo SRE

Instalação do Rancher Desktop via pacote deb Ubuntu 

Installation via .deb Package
Add the Rancher Desktop repository and install Rancher Desktop with:

-curl -s https://download.opensuse.org/repositories/isv:/Rancher:/stable/deb/Release.key | gpg --dearmor | sudo dd status=none of=/usr/share/keyrings/isv--rancher-stable-archive-keyring.gpg
-echo 'deb [signed-by=/usr/share/keyrings/isv-rancher-stable-archive-keyring.gpg] https://download.opensuse.org/repositories/isv:/Rancher:/stable/deb/ ./' | sudo dd status=none of=/etc/apt/sources.list.d/isv-rancher-stable.list
-sudo apt update
-sudo apt install rancher-desktop
