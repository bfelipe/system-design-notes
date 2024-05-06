# Object Store

Object Store is a special database designed to handle large files, such as images, videos, backups, etc. It is an evolution from BLOB (Binary Large Object).

## The file system approach

In operational systems, files are kept inside folders, which holds common related files. Folders can also be stored inside other folders, and have siblings.
This approach usually resemble a tree data structure. Which to access specific file, you need to recursively navigate the tree until you reach the target file.

## The object store approach.

Data is not stored in a hierarquical way as a common system file from an operational system. Instead data is stored in flat addresses which can late be easily acessed through an HTTP request, that will fetch the content the user entity is aiming to handle, instead of directly dealing with the file itself.
In this system, each piece of data is viewed as an object, such as the file itself, metadata, and unique identification.
As you can imagine, files can easily grow in terms of quantity or size. This database can take the advange of its flat architecture to scale, without have to deal with issues related to file size or hierarquical structures.
