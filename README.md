# edlunlock
Unlock any[^1] Qualcomm device with EDL

## Usage 
```bash
./edlunlock -i <DEVICE_PATH> -f <FIREHOSE_PATH> -s <STORAGE_TYPE>
-e|--bkerler : Use bkerler/edl instead of qdl
-f|--firehose : Firehose mbn file, usually named prog.*.ddr.mbn
-i|--device : Device path to the 9008 device, usually /dev/ttyUSB0
-s|--storage : Storage type, either 'emmc', 'nand', or 'ufs'
--relock : Relock device instead of unlocking it
-v : Running version of ./edlunlock
-h : Also shows this message
```
Example:
```bash
./edlunlock -i /dev/ttyUSB0 -f prog_emmc_firehose_8917_ddr.mbn -s emmc
``` 
If you use bkerler mode, you will only need to do:
```bash
./edlunlock --bkerler
```

## How does this work?
On devices that have devinfo, bootloader unlock status is handled by a hex pattern.

Example: 
<table>
  <tr>
    <td>
      <pre><code># Unlocked bootloader
0000000 4e41 5244 494f 2d44 4f42 544f 0021 0000
0000010 0001 0000 0000 0000 0001 0000 0001 0000</code></pre>
    </td>
    <td>
      <pre><code># Locked bootloader
0000000 4e41 5244 494f 2d44 4f42 544f 0021 0000
0000010 0000 0000 0000 0000 0000 0000 0000 0000</code></pre>
    </td>
  </tr>
</table>

# Licensing
This project is licensed under the <a href="https://www.gnu.org/licenses/gpl-3.0.html">GNU General Public License version 3.</a>
<img align="right" src="https://www.gnu.org/graphics/gplv3-127x51.png" alt="GPLv3 logo">

<br>

[^1]: Relies on noauth/bypassed EDL + devinfo
