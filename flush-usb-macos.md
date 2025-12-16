
1. **Open Terminal**

2. Plug in USB then list disks:

   ```bash
   diskutil list
   ```

3. Identify your USB drive (e.g., `/dev/disk2`).

4. Unmount it:

   ```bash
   diskutil unmountDisk /dev/diskN
   ```

   *(replace `N` with your disk number)*

5. Write the ISO:

   ```bash
   sudo dd if=/path/to/your.iso of=/dev/rdiskN bs=1m
   ```

6. When done, eject it:

   ```bash
   diskutil eject /dev/diskN
   ```

This works for *most* ISO files (Linux, rescue tools, etc.). ([nednet.org.uk][6])
