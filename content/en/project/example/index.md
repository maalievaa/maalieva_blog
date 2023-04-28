---
title: Overview of directory operations and methods for implementing directories in file systems
summary: ''
tags:
  - Deep Learning
date: '2023-04-28T00:00:00Z'

# Optional external URL for project (replaces project detail page).
external_link: ''

image:
  caption: Photo by rawpixel on Unsplash
  focal_point: Smart

# Slides (optional).
#   Associate this project with Markdown slides.
#   Simply enter your slide deck's filename without extension.
#   E.g. `slides = "example-slides"` references `content/slides/example-slides.md`.
#   Otherwise, set `slides = ""`.
slides: example
---

## Structure of file systems
In this topic, you need to start with the file system and its structure. A file system is a tool that allows the operating system and programs to access and work with the necessary files. The main functions of the file system:
1) Fragmentation of files and their distribution on the media
2) Search for a file at the request of programs
3) Participation in creating, reading and deleting files
4) Working with file attributes: changing the name, size, last modified time, file access and much more
5) Cataloging and organizing files

The structure of the service data of a file system, for example Unix, on one of the disk partitions can consist of four main parts. At the beginning of the section there is a superblock that contains a description of the file system (for example, it contains information about the type of file system, the size of the file system in blocks, and so on). The presence of the second block allows you to access the data on the disk as a full-fledged file system, and not as a sequence of blocks. The array of index nodes (the third block) contains a list of indexes corresponding to the files of this file system, the size of this array is determined during system installation, and the maximum number of files that can be created in the file system is determined by the number of available index nodes. Files and directories are stored in data blocks.

## What is a directory?

Sometimes the concept of a directory is confused with the concept of a regular file, but a file is an information block that has its own name, logical representation and a unique set of attributes. A directory is a file that looks like a table and stores a list of its directories and files, it serves to maintain the tree structure of the file system.

## Overview of directory operations

The set of operations for managing directories depends on the specifics of a particular OS. Let's consider as an example some system calls that are necessary in the work:
• Creating a directory
To create directories in Linux, the mkdir command is used
• Deleting a directory
To delete, you can use two commands: rmdir, if the directory is empty, and rm, if you need to delete the specified directory along with all attached files and directories
• Opening a directory for later reading
Using the ls command, we can view the contents of the directory
• Renaming
Directory names can be changed, as well as file names. To do this, the mv command can be used, after which the current name of the directory is indicated, and then the new name.
• Creating a file
When creating a new file, you need to add the appropriate element to the directory. Using the touch command, you can create a new file in the directory.
• Deleting a file from a directory
It is worth noting that if the deleted file is present only in one directory, then it is generally deleted from the file system, in another case, the system is limited only to deleting the specified entry. The rm command is used to delete files.

## Methods of implementing a directory in the file system

To access the file, the OS uses the path that the user told it. A directory entry links the file name (or subdirectory name) to the data blocks on the disk, depending on how the disk blocks are allocated to the file, this link can be the number of the first block or the number of the index node. In any case, the symbolic file name is associated with the data on the disk.


