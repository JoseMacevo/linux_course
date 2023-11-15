### Soft links or symlinks (symbolics).

Los vinculos suaves -soft (o simbolicos) se crean utilizando la opcion **-s**.

- **ln -s file1 file3** -> creacion del softlink
- **ls -li file1 file3** -> test del softlink



Los enlaces simbolicos no ocupan espacio adicional en el sistema, son muy utiles ya que se pueden modificar facilmente para apuntar a diferentes lugares.
Una forma sencilla de crear atajos desde /home.

Pueden apuntar a objetos incluso en diferentes sistemas de archivos, particiones y/o discos y otros medios, los cules podrian existir o no, en este ultimo caso se obtendria un ***enlace colgante***.

