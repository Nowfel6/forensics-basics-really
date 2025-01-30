# Hello Juniors,

Hope you all figured out which sector of CTF you are interested in.
If you are interested in Forensics, here are some basic tools to get started!

## **FORENSICS**
In a CTF context, "Forensics" challenges can include file format analysis, steganography, memory dump analysis, or network packet capture analysis. Any challenge that requires extracting hidden information from static data files could be considered a Forensics challenge.

### **Requisite Skills**
To solve Forensics CTF challenges, the two most useful abilities are:
1. Knowing how to manipulate binary data (byte-level manipulations) in a programming language.
2. Recognizing formats, protocols, structures, and encodings of a file.

---
## **Common Forensics Concepts and Tools**

### **1. File Format Identification ("Magic Bytes")**
Almost every forensics challenge will involve a file, usually without a proper extension. The traditional method for identifying file types on UNIX systems is **libmagic**, which is used by the `file` command.

#### **Example:**
```sh
$ file screenshot.png
screenshot.png: PNG image data, 1920 x 1080, 8-bit/color RGBA, non-interlaced
```

---
### **2. File Carving**
File carving is the process of extracting embedded files from another file. One of the best tools for this task is `binwalk`.

#### **Example:**
```sh
$ binwalk flag.png
```
**Output:**
```
DECIMAL       HEXADECIMAL     DESCRIPTION
--------------------------------------------------------------------------------
0            0x0             PNG image, 500 x 500, 8-bit/color RGB, non-interlaced
1024         0x400           Zip archive data, at least v2.0 to extract
```

To extract embedded files, use:
```sh
$ binwalk -e flag.png
```

---
### **3. Initial Analysis**
If you don't have any initial clues, you can use `strings` to find readable text in binary files.

#### **Example:**
```sh
$ strings flag.elf | grep Cuet_CTF{
```

---
### **4. Common File Formats**

To be prepared for most CTF Forensics challenges, you should be familiar with the following file formats:

- Archive files (**ZIP, TGZ, RAR**)
- Image file formats (**JPG, PNG, BMP**)
- Filesystem images (**EXT4**)
- Packet captures (**PCAP, PCAPNG**)
- Memory dumps
- PDFs
- Video (**MP4**) or Audio (**MP3, WAV**)
- Microsoft Office formats (**RTF, OLE, OOXML**)

---
### **5. Archive Files**
Sometimes, a challenge may involve extracting a corrupted or encrypted archive. The `unzip` command can provide useful error messages.

#### **Example:**
```sh
$ unzip flag.zip
```
**Output:**
```
Archive:  flag.zip
  inflating: flag.txt  
```

To list files inside a ZIP archive without extracting:
```sh
$ unzip -l flag.zip
```
**Output:**
```
Archive:  flag.zip
  Length      Date    Time    Name
---------  ---------- -----   ----
       35  2025-01-30 12:00   flag.txt
---------                     -------
       35                     1 file
```

---
### **6. Image File Format Analysis**
Since image files are common in CTFs, tools like `exiftool` help extract metadata.

#### **Example:**
```sh
$ exiftool screenshot.png
```
**Output (Truncated):**
```
File Name                       : screenshot.png
File Size                       : 750 kB
File Type                       : PNG
MIME Type                       : image/png
Image Width                     : 1482
Image Height                    : 648
Compression                     : Deflate/Inflate
Exif Image Width                : 1482
Exif Image Height               : 648
Image Size                      : 1482x648
```

---

This guide should help you get started with Forensics challenges in CTF competitions. Happy hacking!
