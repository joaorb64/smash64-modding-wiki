<style>
.gfx-table {
  width: 100%;
  border-collapse: collapse;
}

.gfx-table th,
.gfx-table td {
  border: 1px solid #e0e0e0;
  padding: 8px;
  text-align: left;
}

.gfx-table th {
  font-weight: bold;
}

.gfx-table td:first-child {
  width: 60px;
  text-align: center;
}

.gfx-table th:last-child,
.gfx-table td:last-child {
  text-align: right;
  width: 200px;
}
</style>

# GFX Moveset Commands

## Overview

The GFX command is used to display visual effects in movesets. The command starts with `0x98` or `0x9A` and contains the following parameters:

| Parameter  | Description                              |
| ---------- | ---------------------------------------- |
| flag       | Effect flags/modifiers                   |
| bone       | Bone attachment point                    |
| effect id  | Effect ID to display                     |
| x1, y1, z1 | Location (position where effect appears) |
| x2, y2, z2 | Spread (effect size/spread distance)     |

## Vanilla Effects

<table class="gfx-table">
<thead>
<tr>
<th style="width: 60px;">ID</th>
<th>Effect</th>
<th style="width: 200px;">Video</th>
</tr>
</thead>
<tbody>
<tr><td>0x0</td><td>hit</td><td><video width="200" autoplay loop controls><source src="0x0.webm" type="video/webm"></video></td></tr>
<tr><td>0x18</td><td>burn</td><td><video width="200" autoplay loop controls><source src="0x18.webm" type="video/webm"></video></td></tr>
<tr><td>0x1C</td><td>smoke</td><td><video width="200" autoplay loop controls><source src="0x1C.webm" type="video/webm"></video></td></tr>
<tr><td>0x20</td><td>smoke</td><td><video width="200" autoplay loop controls><source src="0x20.webm" type="video/webm"></video></td></tr>
<tr><td>0x28</td><td>electricity</td><td><video width="200" autoplay loop controls><source src="0x28.webm" type="video/webm"></video></td></tr>
<tr><td>0x2C</td><td>slide smoke</td><td><video width="200" autoplay loop controls><source src="0x2C.webm" type="video/webm"></video></td></tr>
<tr><td>0x30</td><td>quick slide smoke</td><td><video width="200" autoplay loop controls><source src="0x30.webm" type="video/webm"></video></td></tr>
<tr><td>0x34</td><td>landing smoke</td><td><video width="200" autoplay loop controls><source src="0x34.webm" type="video/webm"></video></td></tr>
<tr><td>0x38</td><td>quick landing smoke (front one is faster?)</td><td><video width="200" autoplay loop controls><source src="0x38.webm" type="video/webm"></video></td></tr>
<tr><td>0x3C</td><td>forward only landing smoke</td><td><video width="200" autoplay loop controls><source src="0x3C.webm" type="video/webm"></video></td></tr>
<tr><td>0x40</td><td>back only landing smoke</td><td><video width="200" autoplay loop controls><source src="0x40.webm" type="video/webm"></video></td></tr>
<tr><td>0x44</td><td>big, slow smoke</td><td><video width="200" autoplay loop controls><source src="0x44.webm" type="video/webm"></video></td></tr>
<tr><td>0x48</td><td>small, in-place smoke</td><td><video width="200" autoplay loop controls><source src="0x48.webm" type="video/webm"></video></td></tr>
<tr><td>0x4C</td><td>dash smoke</td><td><video width="200" autoplay loop controls><source src="0x4C.webm" type="video/webm"></video></td></tr>
<tr><td>0x50</td><td>big dash smoke</td><td><video width="200" autoplay loop controls><source src="0x50.webm" type="video/webm"></video></td></tr>
<tr><td>0x54</td><td>blueish gray balls</td><td><video width="200" autoplay loop controls><source src="0x54.webm" type="video/webm"></video></td></tr>
<tr><td>0x58</td><td>ground bump</td><td><video width="200" autoplay loop controls><source src="0x58.webm" type="video/webm"></video></td></tr>
<tr><td>0x5C</td><td>ice-like shards (back)</td><td><video width="200" autoplay loop controls><source src="0x5C.webm" type="video/webm"></video></td></tr>
<tr><td>0x60</td><td>ice-like shards (forward)</td><td><video width="200" autoplay loop controls><source src="0x60.webm" type="video/webm"></video></td></tr>
<tr><td>0x64</td><td>ice-like shards (back)</td><td><video width="200" autoplay loop controls><source src="0x64.webm" type="video/webm"></video></td></tr>
<tr><td>0x68</td><td>earth?-like shards (forward)</td><td><video width="200" autoplay loop controls><source src="0x68.webm" type="video/webm"></video></td></tr>
<tr><td>0x6C</td><td>earth?-like shards (back)</td><td><video width="200" autoplay loop controls><source src="0x6C.webm" type="video/webm"></video></td></tr>
<tr><td>0x70</td><td>explosion</td><td><video width="200" autoplay loop controls><source src="0x70.webm" type="video/webm"></video></td></tr>
<tr><td>0x74</td><td>explosion (multiple)</td><td><video width="200" autoplay loop controls><source src="0x74.webm" type="video/webm"></video></td></tr>
<tr><td>0x78</td><td>explosion (multiple) (small)</td><td><video width="200" autoplay loop controls><source src="0x78.webm" type="video/webm"></video></td></tr>
<tr><td>0x7C</td><td>flash</td><td><video width="200" autoplay loop controls><source src="0x7C.webm" type="video/webm"></video></td></tr>
<tr><td>0x80</td><td>quake (small)</td><td><video width="200" autoplay loop controls><source src="0x80.webm" type="video/webm"></video></td></tr>
<tr><td>0x84</td><td>quake (big)</td><td><video width="200" autoplay loop controls><source src="0x84.webm" type="video/webm"></video></td></tr>
<tr><td>0x88</td><td>quake (bigger)</td><td><video width="200" autoplay loop controls><source src="0x88.webm" type="video/webm"></video></td></tr>
<tr><td>0x94</td><td>samus shoot fire</td><td><video width="200" autoplay loop controls><source src="0x94.webm" type="video/webm"></video></td></tr>
<tr><td>0xA0</td><td>flash (yellow-ish)</td><td><video width="200" autoplay loop controls><source src="0xA0.webm" type="video/webm"></video></td></tr>
<tr><td>0xA4</td><td>flash with circle</td><td><video width="200" autoplay loop controls><source src="0xA4.webm" type="video/webm"></video></td></tr>
<tr><td>0xA8</td><td>green circle (ledge grab?)</td><td><video width="200" autoplay loop controls><source src="0xA8.webm" type="video/webm"></video></td></tr>
<tr><td>0xAC</td><td>green circle (big)</td><td><video width="200" autoplay loop controls><source src="0xAC.webm" type="video/webm"></video></td></tr>
<tr><td>0xB0</td><td>green circle (bigger)</td><td><video width="200" autoplay loop controls><source src="0xB0.webm" type="video/webm"></video></td></tr>
<tr><td>0xB8</td><td>wood particles (box item destroyed)</td><td><video width="200" autoplay loop controls><source src="0xB8.webm" type="video/webm"></video></td></tr>
<tr><td>0xBC</td><td>crashes game</td><td><video width="200" autoplay loop controls><source src="0xBC.webm" type="video/webm"></video></td></tr>
<tr><td>0xD8</td><td>star</td><td><video width="200" autoplay loop controls><source src="0xD8.webm" type="video/webm"></video></td></tr>
<tr><td>0x118</td><td>point score "ki" effect</td><td><video width="200" autoplay loop controls><source src="0x118.webm" type="video/webm"></video></td></tr>
<tr><td>0x11C</td><td>blue circle shrink-grow</td><td><video width="200" autoplay loop controls><source src="0x11C.webm" type="video/webm"></video></td></tr>
<tr><td>0x128</td><td>heal sparks (sometimes only one flash)</td><td><video width="200" autoplay loop controls><source src="0x128.webm" type="video/webm"></video></td></tr>
<tr><td>0x168</td><td>music note</td><td><video width="200" autoplay loop controls><source src="0x168.webm" type="video/webm"></video></td></tr>
<tr><td>0x16C</td><td>rock shards</td><td><video width="200" autoplay loop controls><source src="0x16C.webm" type="video/webm"></video></td></tr>
</tbody>
</table>

## Smash Remix Effects

<table class="gfx-table">
<thead>
<tr>
<th style="width: 60px;">ID</th>
<th>Effect</th>
<th style="width: 200px;">Video</th>
</tr>
</thead>
<tbody>
<tr><td>0x170</td><td>dark explosion</td><td><video width="200" autoplay loop controls><source src="0x170.webm" type="video/webm"></video></td></tr>
<tr><td>0x174</td><td>dark explosion (multiple)</td><td><video width="200" autoplay loop controls><source src="0x174.webm" type="video/webm"></video></td></tr>
<tr><td>0x178</td><td>dark smoke (forward)</td><td><video width="200" autoplay loop controls><source src="0x178.webm" type="video/webm"></video></td></tr>
<tr><td>0x17C</td><td>dark smoke (back)</td><td><video width="200" autoplay loop controls><source src="0x17C.webm" type="video/webm"></video></td></tr>
<tr><td>0x180</td><td>dark smoke (down-back)</td><td><video width="200" autoplay loop controls><source src="0x180.webm" type="video/webm"></video></td></tr>
<tr><td>0x184</td><td>dark smoke (down-forward)</td><td><video width="200" autoplay loop controls><source src="0x184.webm" type="video/webm"></video></td></tr>
<tr><td>0x188</td><td>dark smoke</td><td><video width="200" autoplay loop controls><source src="0x188.webm" type="video/webm"></video></td></tr>
<tr><td>0x18C</td><td>dark smoke (small)</td><td><video width="200" autoplay loop controls><source src="0x18C.webm" type="video/webm"></video></td></tr>
<tr><td>0x190</td><td>dark ground bump</td><td><video width="200" autoplay loop controls><source src="0x190.webm" type="video/webm"></video></td></tr>
<tr><td>0x194</td><td>purple smoke</td><td><video width="200" autoplay loop controls><source src="0x194.webm" type="video/webm"></video></td></tr>
<tr><td>0x198</td><td>dr mario pill explosion</td><td><video width="200" autoplay loop controls><source src="0x198.webm" type="video/webm"></video></td></tr>
<tr><td>0x19C</td><td>Lucas PK effect</td><td><video width="200" autoplay loop controls><source src="0x19C.webm" type="video/webm"></video></td></tr>
<tr><td>0x1A0</td><td>Lucas PK effect (upwards)</td><td><video width="200" autoplay loop controls><source src="0x1A0.webm" type="video/webm"></video></td></tr>
<tr><td>0x1A4</td><td>Lucas PK effect (tiny)</td><td><video width="200" autoplay loop controls><source src="0x1A4.webm" type="video/webm"></video></td></tr>
<tr><td>0x1A8</td><td>purple flash</td><td><video width="200" autoplay loop controls><source src="0x1A8.webm" type="video/webm"></video></td></tr>
<tr><td>0x1AC</td><td>purple smoke</td><td><video width="200" autoplay loop controls><source src="0x1AC.webm" type="video/webm"></video></td></tr>
<tr><td>0x1B0</td><td>purple cross</td><td><video width="200" autoplay loop controls><source src="0x1B0.webm" type="video/webm"></video></td></tr>
<tr><td>0x1B4</td><td>purple fire</td><td><video width="200" autoplay loop controls><source src="0x1B4.webm" type="video/webm"></video></td></tr>
<tr><td>0x1B8</td><td>purple flash with circle</td><td><video width="200" autoplay loop controls><source src="0x1B8.webm" type="video/webm"></video></td></tr>
<tr><td>0x1BC</td><td>tiny pink smoke</td><td><video width="200" autoplay loop controls><source src="0x1BC.webm" type="video/webm"></video></td></tr>
<tr><td>0x1C0</td><td>huge white smoke</td><td><video width="200" autoplay loop controls><source src="0x1C0.webm" type="video/webm"></video></td></tr>
<tr><td>0x1C4</td><td>yellow flash</td><td><video width="200" autoplay loop controls><source src="0x1C4.webm" type="video/webm"></video></td></tr>
<tr><td>0x1C8</td><td>crashes game</td><td><video width="200" autoplay loop controls><source src="0x1C8.webm" type="video/webm"></video></td></tr>
<tr><td>0x1CC</td><td>red sparkles</td><td><video width="200" autoplay loop controls><source src="0x1CC.webm" type="video/webm"></video></td></tr>
<tr><td>0x1D0</td><td>red flash with back smoke</td><td><video width="200" autoplay loop controls><source src="0x1D0.webm" type="video/webm"></video></td></tr>
<tr><td>0x1D4</td><td>red heal</td><td><video width="200" autoplay loop controls><source src="0x1D4.webm" type="video/webm"></video></td></tr>
<tr><td>0x1D8</td><td>feather</td><td><video width="200" autoplay loop controls><source src="0x1D8.webm" type="video/webm"></video></td></tr>
<tr><td>0x1DC</td><td>feather variation</td><td><video width="200" autoplay loop controls><source src="0x1DC.webm" type="video/webm"></video></td></tr>
<tr><td>0x1E0</td><td>2 feathers</td><td><video width="200" autoplay loop controls><source src="0x1E0.webm" type="video/webm"></video></td></tr>
<tr><td>0x1E4</td><td>yellow sparkles</td><td><video width="200" autoplay loop controls><source src="0x1E4.webm" type="video/webm"></video></td></tr>
<tr><td>0x1E8</td><td>yellow flash with back smoke</td><td><video width="200" autoplay loop controls><source src="0x1E8.webm" type="video/webm"></video></td></tr>
<tr><td>0x1EC</td><td>yellow heal</td><td><video width="200" autoplay loop controls><source src="0x1EC.webm" type="video/webm"></video></td></tr>
<tr><td>0x1F0</td><td>yellow puff</td><td><video width="200" autoplay loop controls><source src="0x1F0.webm" type="video/webm"></video></td></tr>
<tr><td>0x1F4</td><td>light sparkle</td><td><video width="200" autoplay loop controls><source src="0x1F4.webm" type="video/webm"></video></td></tr>
</tbody>
</table>
