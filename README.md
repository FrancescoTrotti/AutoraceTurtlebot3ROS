# Progetto Cyberfisico
## Autonomous drive turtlebot3
Francesco Trotti VR398637 <br>
Moreno Bragaglio VR423929

## Prerequisiti
- ROS
- catkin
- OpenCV

## Esecuzione:
- Clonare la repository di gitHub: git clone https://github.com/FrancescoTrotti/AutoraceTurtlebot3ROS.git
- Compilare catkin: catkin_make
- Aprire un terminale ed eseguire: roscore
- Aprire un secondo terminale ed eseguire: export TURTLEBOT3_MODEL=burger_pi
- Sempre sul secondo terminale eseguire: roslaunch autorace gazebo.launch
- Aprire un terzo terminale ed eseguire: export TURTLEBOT3_MODEL=burger_pi
- Sempre sul terzo terminale eseguire: roslaunch autorace autorace.launch

## Obiettivo:
Il progetto consiste nel riprodurre il codice creato dalla ROBOTIS per l'autonomous drive del turtlebot3. Questo deve seguire un 
percorso prestabilito limitato da due linee bianche e muovendosi in autonomia.

## Sviluppo:
Abbiamo modificato il codice della ROBOTIS e selezionato solo i nodi essenziali per la la guida autonoma. 
I nodi che abbiamo selezionato sono: <br>
- image_projection.py <br>
In questo nodo viene applicata una matrice di omografia hai frame catturati dalla camera del turtlebot3 così da eliminare la prospettiva delle linee create nei frame originali
- detect_lane.py <br>
In questo codice è stata reimplementata la line detection utilizzando funzioni di openCV ad esempio thresholding e HoughLinesP. Inoltre è stato calcolato il punto medio delle linee riconosciute cosi da 
creare una linea centrale (gialla) da seguire per il turtlebot3. Problema riscontrato è che la line detection fatta dalla funzione HoughLinesP() è probabilistica quindi ad ogni ciclo di codice il valore dei punti cambia 
spostando la linea gialla, per ovviare questo problema abbiamo normalizzato i punti facendo la media tra i massimi e minimi dei punti e tracciata di nuovo la retta risultando cosi sempre al centro delle due righe bianche. <br>

##Autorace turtlebot3 video demo <br>
https://drive.google.com/file/d/1N0VpxieBVTNEEMXPVaMwxylHk9UehXIT/view?usp=sharing
