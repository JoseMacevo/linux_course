### Hard Links

The **ln** utility is used for create **hard_links** and (with **-s*** option **soft_links**), also known as **symbolic_links or symlinks**. 
1. We create a file or we can use a file previously created.
2. ln file1 file2 -> hard_link creation.
3. We check the link with the **-i** option in the **ls** command, this print the inodo number, unique for each file object, in this case it's the same.
4. ls -li file1 file2 -> hard_link test.

