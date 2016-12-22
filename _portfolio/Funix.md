---
title: "Funix"
header:
  teaser: assets/images/funix.PNG
---
A faithful replica of the Bash CLI, written in C++ for my Object Oriented Programming class.  

Extensive use of classes, inheritance, and pointers.  

### Supported commands/concepts:
- cd  
- mkdir  
- rm  
- ls  
- touch  
- chmod  
- su  
- chown  
- Persistent directories via file I/O (even after closing the simulation)  
- Timestamps  
- Permissions + Users (full rwx behavior, recursively applied to subfolders too)  



## Here's some code:

```c++
void Directory::cp(int argCount, const char *arguments[], const char *user)
{
  if (!iscpCorrectFormat(argCount, arguments))
    return;
  for (int i = 0; i < subDirectoryCount; i++) //check arguments 
  {
    Directory *directory = dynamic_cast<Directory*> (subDirectories[i]);
    if (*subDirectories[i] == Directory(arguments[1])) //if 1st argument exists in subdirs[]
    {
      if (!subDirectories[i]->getPermissions()->isPermitted(READ_PERMISSIONS, user ))
      { //if you have permissions to copy it
        cout << "cp: cannot open ‘" << arguments[1] << "’ for reading: Permission denied\n";
        return;
      }  // if not allowed to read
      
      if (directory){    
        Directory *destinationDirectory = new Directory(*directory); //calls dir copy constructor
        delete [] destinationDirectory->name;
        destinationDirectory->name = new char[strlen(arguments[2]) + 1];
        strcpy(destinationDirectory->name, arguments[2]);
        directory->name = new char[strlen(arguments[1]) + 1];
        strcpy(directory->name, arguments[1]);
        subDirectories += destinationDirectory;
        subDirectoryCount++;
        return;
      }
      else
      {
        File *destinationFile = new File(*subDirectories[i], arguments[2]);
        subDirectories += destinationFile;
        subDirectoryCount++;
        return;
      }  // if found source subdirectory
    }
  } // for each subdirectory
  
  cout << "cp: cannot stat ‘" << arguments[1] << "’: No such file or directory\n";
  cout << "Try 'cp --help' for more information.\n";
}  // cp()

```
Full source available on request.