# iriunwebcam_fedora40 
iriun webcam para fedora 40 / 100% probado.
Realiza cada uno de estos pasos uno a uno
## 1) En primer lugar debes descargar el software de iriun webcam prporcionado aqui con la extension .rpm
   
## 2) En segundo lugar abres tu "Konsole_Terminal" exactammnte en el directorio donde esta tu archivo. normalmente lo debes tener e la carpeta descargas.
   
## 3) vas a instalar usando este comando en la terminal:
sudo rpm -Uvh (nombre_del_paquete) --force
cierra esa terminal.

## 4) abre una nueva Terminal, utiliza este comando luego de abrirla:
cd /
cd home

## 5) crearas una bash file (en tu directorio home) con el siguiente comando:
touch iriun.sh

## 6) editas la bash file
nano iriun.sh

## 7) Pegas esta linea con (Ctrl+Shift+V):
sudo rmmod v4l2loopback && sudo modprobe v4l2loopback exclusive_caps=1

luego con Ctrl + o (guardas), presionas Enter (para_ok), y sales con Ctrl + X (salida)

Make it executable:
sudo chmod +x iriun.sh

## 8) luego colocas en este orde los comandos: 
sudo dnf makecache --refresh
sudo dnf install make
sudo dnf install dkms

## 9) no cierres esta terminal, mantenla abierta en el directorio home. Pero Abre otra terminal como super usuario (sudo -i) y ejecuta los siguientes comandos:
sudo dnf install kernel-devel kernel-headers dkms v4l-utils
git clone https://github.com/umlaeute/v4l2loopback.git
cd v4l2loopback
make
sudo cp -R . /usr/src/v4l2loopback-1.1
sudo dkms add -m v4l2loopback -v 1.1
sudo dkms build -m v4l2loopback -v 1.1
sudo dkms install -m v4l2loopback -v 1.1

## 10) Reinicia tu sistema con este comando:
reboot

## 11)Después de reiniciar, ejecuta los siguientes comandos:
sudo depmod -a
sudo modprobe v4l2loopback card_label="Camera"

## 12) desde la terminal en el directorio Home, Every time you want to open the Iriun Webcam run, este paso es muy importante:
./iriun.sh

Luego ve y abre tu aplicacion, recuerda haber conectado primero tu Smart Phone y abrir Irun en el. y listooooo a gozrte.
