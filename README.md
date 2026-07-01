# esp32-firmware-carving
Craved or dump any information from the esp32 firmware.

# Installation 
> linux or termux (ubuntu/debian proot)
```
sudo apt install && sudo apt install binwalk -y
```
- Download any firmware you want to dump the info and execute
```
binwalk --term firmware.bin
```
- Extract all the partitions
```
binwalk --term --dd='.*' firmware.bin --run-as=root
```
- cd to the extracted directory
```
cd _*
```
- Dump extracted data information
```
file * > data.txt
cat data.txt
```
- Select the 0x10000 firmware partitions
```
strings 8040 | grep -i "\.h\|\.cpp"
```

### Output
```
DECIMAL       HEXADECIMAL     DESCRIPTION
----------------------------------------------------------------------------------------------------------
4096          0x1000          ESP Image (ESP32): segment count: 3, flash mode: DIO, flash speed: 80MHz,
                              flash size: 4MB, entry address: 0x400805b4, hash: sha256
32768         0x8000          ESP32 Partition Table Entry: label: "nvs", type: DATA, subtype: NVS,
                              offset: 0x9000, size: 0x5000, flags: 0x0 (not encrypted)
32800         0x8020          ESP32 Partition Table Entry: label: "otadata", type: DATA, subtype:
                              Factory/OTA DATA, offset: 0xe000, size: 0x2000, flags: 0x0 (not encrypted)
32832         0x8040          ESP32 Partition Table Entry: label: "app0", type: APP, subtype: OTA 0,
                              offset: 0x10000, size: 0x140000, flags: 0x0 (not encrypted)
32864         0x8060          ESP32 Partition Table Entry: label: "app1", type: APP, subtype: OTA 1,
                              offset: 0x150000, size: 0x140000, flags: 0x0 (not encrypted)
32896         0x8080          ESP32 Partition Table Entry: label: "spiffs", type: DATA, subtype: SPIFFS,
                              offset: 0x290000, size: 0x160000, flags: 0x0 (not encrypted)
32928         0x80A0          ESP32 Partition Table Entry: label: "coredump", type: DATA, subtype:
                              Coredump, offset: 0x3f0000, size: 0x10000, flags: 0x0 (not encrypted)
65536         0x10000         ESP Image (ESP32): segment count: 6, flash mode: DIO, flash speed: 80MHz,
                              flash size: 4MB, entry address: 0x40081ff4, hash: sha256
67962         0x1097A         HTML document header
70852         0x114C4         HTML document footer
70860         0x114CC         HTML document header
71164         0x115FC         HTML document footer
76645         0x12B65         Base64 standard index table
116557        0x1C74D         Neighborly text, "neighbor entryetif/ethernet.c"
156481        0x26341         PEM RSA private key
156542        0x2637E         PEM EC private key
156599        0x263B7         PEM PKCS#8 private key
157713        0x26811         PEM certificate
159790        0x2702E         AU audio data, 1694523760 sample rate, 779119974 channels
159862        0x27076         AU audio data, 1634625907 sample rate, 1936028672 channels
162343        0x27A27         HTML document header
168518        0x29246         HTML document footer
168541        0x2925D         HTML document header
200372        0x30EB4         HTML document footer
200396        0x30ECC         HTML document header
202028        0x3152C         HTML document footer
235716        0x398C4         SHA256 hash constants, little endian
237112        0x39E38         AES Inverse S-Box
237624        0x3A038         AES S-Box
590612        0x90314         ELF, 32-bit LSB processor-specific, ("4")

1000:  DOS executable (COM), start instruction 0xe903022f b4050840
10000: ESP-IDF application image for ESP32, project name: "arduino-lib-builder", version 8cabf2c, compiled on Feb 11 2026 19:51:20, IDF version: v5.5.2-729-g87912cd291, entry address: 0x40081FF4
1097A: data
114C4: data
114CC: data
115FC: data
12B65: data
1C74D: data
26341: PEM RSA private key
2637E: PEM EC private key
263B7: OpenSSH private key (no password)
26811: PEM certificate
2702E: Sun/NeXT audio data: 1694523760 Hz
27076: Sun/NeXT audio data: 1634625907 Hz
27A27: data
29246: data
2925D: data
30EB4: data
30ECC: data
3152C: data
398C4: OpenPGP Public Key
39E38: data
3A038: data
8000:  ESP-IDF partition table entry, label: "nvs", NVS data, offset: 0x9000, size: 0x5000
8020:  ESP-IDF partition table entry, label: "otadata", OTA selection data, offset: 0xE000, size: 0x2000
8040:  ESP-IDF partition table entry, label: "app0", OTA_0 app, offset: 0x10000, size: 0x140000
8060:  ESP-IDF partition table entry, label: "app1", OTA_1 app, offset: 0x150000, size: 0x140000
8080:  ESP-IDF partition table entry, label: "spiffs", SPIFFS partition, offset: 0x290000, size: 0x160000
80A0:  ESP-IDF partition table entry, label: "coredump", coredump data, offset: 0x3F0000, size: 0x10000
90314: ELF 32-bit LSB *unknown arch 0x3f40* (SYSV)
/C:\Users\N&R SOLARTECH SOL\AppData\Local\Arduino15\packages\esp32\hardware\esp32\3.3.7\libraries\WebServer\src\Parsing.cpp
C:\Users\N&R SOLARTECH SOL\AppData\Local\Arduino15\packages\esp32\tools\esp32-libs\3.3.7/include/hal/esp32/include/hal/i2c_ll.h
C:\Users\N&R SOLARTECH SOL\AppData\Local\Arduino15\packages\esp32\tools\esp32-libs\3.3.7/include/hal/esp32/include/hal/timer_ll.h
//IDF/components/hal/esp32/include/hal/gpio_ll.h
//IDF/components/hal/esp32/include/hal/rtc_io_ll.h
/IDF/components/hal/esp32/include/hal/cache_ll.h
//IDF/components/heap/tlsf/tlsf_block_functions.h
//IDF/components/heap/tlsf/tlsf_control_functions.h
//IDF/components/esp_hw_support/include/esp_cpu.h
/IDF/components/hal/esp32/include/hal/rtc_cntl_ll.h
//IDF/components/freertos/esp_additions/freertos_tasks_c_additions.h
/IDF/components/hal/esp32/include/hal/timer_ll.h
!(is_rs485_mode && disabled && uart_hal_get_intraw_mask(&(uart_context[uart_num].hal)) & UART_INTR_TX_DONE)
//IDF/components/nvs_flash/src/nvs_api.cpp
Increase LWIP_NUM_NETIF_CLIENT_DATA in lwipopts.h
/IDF/components/hal/esp32/include/hal/i2c_ll.h
ap.hidden
sta.he_dcm
sta.he_dcm_c_tx
sta.he_dcm_c_rx
sta.he_mcs9_d
sta.he_su_b_d
sta.he_su_b_f_d
sta.he_mu_b_f_d
sta.he_cqi_f_d
/IDF/components/hal/esp32/include/hal/mpi_ll.h
u<!DOCTYPE html><html><head><meta name="viewport" content="width=device-width,initial-scale=1,maximum-scale=1,user-scalable=no"><title>Diagnostic</title><style>*{box-sizing:border-box;margin:0;padding:0}body{font-family:system-ui,sans-serif;background:#0f172a;color:#e2e8f0;font-size:12px;padding:8px;max-height:100vh;overflow:hidden}.h{text-align:center;color:#f59e0b;font-size:16px;font-weight:700;margin-bottom:8px}.g{display:grid;grid-template-columns:1fr 1fr;gap:6px}.c{background:#1e293b;border-radius:8px;padding:8px}.ct{color:#38bdf8;font-size:11px;font-weight:600;margin-bottom:6px;border-bottom:1px solid #334155;padding-bottom:4px}.r{display:flex;gap:6px;flex-wrap:wrap;justify-content:center}.b{padding:10px 14px;border:none;border-radius:6px;font-size:12px;font-weight:600;cursor:pointer;min-width:48px;transition:all 0.1s}.bp{background:#0ea5e9;color:#fff}.bg{background:#22c55e;color:#fff}.br{background:#ef4444;color:#fff}.by{background:#f59e0b;color:#fff}.bon{background:#22c55e;color:#fff;box-shadow:0 0 8px #22c55e}.b:active{transform:scale(.95)}.i{display:inline-flex;align-items:center;justify-content:center;width:36px;height:36px;border-radius:50%;margin:3px;font-weight:700;font-size:12px}.ion{background:#22c55e;color:#fff;box-shadow:0 0 10px #22c55e}.ioff{background:#334155;color:#64748b}.st{font-size:10px;color:#94a3b8;text-align:center;margin-top:4px}.sterr{font-size:10px;color:#ef4444;text-align:center;margin-top:4px;font-weight:bold}.bk{margin-top:8px;text-align:center}.bk a{color:#38bdf8;font-size:11px}.sel{padding:6px;border-radius:4px;background:#0f172a;color:#e2e8f0;border:1px solid #334155;font-size:11px}</style></head><body><div class="h">DIAGNOSTIC MODE (LCD)</div><div class="g"><div class="c"><div class="ct">BUTTONS GPIO 25,26,27,14</div><div class="r" id="btns"></div><div class="st">Press physical button</div></div><div class="c"><div class="ct">SENSOR GPIO15</div><div class="r"><span class="i ioff" id="sens">--</span></div><div class="st" id="sensv">Waiting...</div></div><div class="c"><div class="ct">SENSOR LED GPIO2</div><div class="r"><button class="b bg" onclick="tst('sled',1)">ON</button><button class="b br" onclick="tst('sled',0)">OFF</button><button class="b by" onclick="tst('sled',2)">BLINK</button></div></div><div class="c"><div class="ct">LED FRAME GPIO13</div><div class="r"><button class="b bg" onclick="tst('ledf',1)">ON</button><button class="b br" onclick="tst('ledf',0)">OFF</button></div></div><div class="c"><div class="ct">LEDs GPIO 4,32,33,3</div><div class="r" id="leds"></div><div class="r" style="margin-top:6px"><select class="sel" id="leddly"><option value="300">300ms</option><option value="500" selected>500ms</option><option value="1000">1s</option></select><button class="b by" onclick="ledAll()">ALL</button><button class="b br" onclick="ledOff()">OFF</button></div></div><div class="c"><div class="ct">RELAYS GPIO 16,17,18,23</div><div class="r" id="relays"></div><div class="r" style="margin-top:6px"><select class="sel" id="reldly"><option value="300">300ms</option><option value="500" selected>500ms</option><option value="1000">1s</option></select><button class="b by" onclick="relayAll()">ALL</button><button class="b br" onclick="relayOff()">OFF</button></div></div><div class="c"><div class="ct">BUZZER GPIO5</div><div class="r"><button class="b bp" onclick="tst('buz',1)">BEEP</button><button class="b bg" onclick="tst('buz',2)">COIN</button><button class="b by" onclick="tst('buz',3)">START</button><button class="b br" onclick="tst('buz',4)">ERROR</button></div></div><div class="c"><div class="ct">COIN ACCEPTOR GPIO19</div><div class="r"><span style="font-size:22px;font-weight:700;color:#22c55e" id="coin">0</span></div><div class="st" id="coinst">Insert coin to test</div><div class="r" style="margin-top:4px"><button class="b br" onclick="tst('coinrst',0)">RESET</button></div></div><div class="c"><div class="ct">LCD PATTERNS I2C 21,22</div><div class="r"><button class="b bp" onclick="tst('lcd',1)">TEST</button><button class="b bg" onclick="tst('lcd',2)">FILL</button><button class="b by" onclick="tst('lcd',3)">BORDER</button><button class="b bp" onclick="tst('lcd',4)">COUNT</button><button class="b br" onclick="tst('lcd',0)">CLR</button></div></div></div><div class="bk"><a href="/" onclick="exitDiag()">Back to Dashboard</a></div><script>var NS=4,ls=[],rs=[];function $(i){return document.getElementById(i)}function init(){var b='',l='',r='';for(var i=0;i<NS;i++){b+='<span class="i ioff" id="b'+i+'">'+(i+1)+'</span>';l+='<button class="b bp" id="lb'+i+'" onclick="led('+i+')">L'+(i+1)+'</button>';r+='<button class="b bp" id="rb'+i+'" onclick="relay('+i+')">R'+(i+1)+'</button>';ls[i]=0;rs[i]=0}$('btns').innerHTML=b;$('leds').innerHTML=l;$('relays').innerHTML=r}function ld(){fetch('/api/diag/status').then(r=>r.json()).then(d=>{for(var i=0;i<NS;i++){$('b'+i).className=d.buttons[i]?'i ion':'i ioff';if(d.leds){ls[i]=d.leds[i];$('lb'+i).className=d.leds[i]?'b bon':'b bp'}if(d.relays){rs[i]=d.relays[i];$('rb'+i).className=d.relays[i]?'b bon':'b bp'}}$('sens').className=d.sensor?'i ion':'i ioff';$('sens').textContent=d.sensor?'HI':'LO';$('sensv').textContent='GPIO15: '+(d.sensor?'HIGH':'LOW');$('coin').textContent=d.coinPulses;if(d.coinShorted){$('coin').style.color='#ef4444';$('coinst').className='sterr';$('coinst').textContent='SHORT DETECTED! Check wiring'}else{$('coin').style.color='#22c55e';$('coinst').className='st';$('coinst').textContent='Insert coin to test'}}).catch(e=>0)}function tst(t,v){fetch('/api/diag/test',{method:'POST',headers:{'Content-Type':'application/json'},body:JSON.stringify({type:t,value:v})})}function led(i){ls[i]=!ls[i];$('lb'+i).className=ls[i]?'b bon':'b bp';tst('ledon',i)}function ledAll(){tst('ledall',+$('leddly').value)}function ledOff(){for(var i=0;i<NS;i++){ls[i]=0;$('lb'+i).className='b bp'}tst('led',-1)}function relay(i){rs[i]=!rs[i];$('rb'+i).className=rs[i]?'b bon':'b bp';tst('relayon',i)}function relayAll(){tst('relayall',+$('reldly').value)}function relayOff(){for(var i=0;i<NS;i++){rs[i]=0;$('rb'+i).className='b bp'}tst('relay',-1)}function exitDiag(){tst('exit',0)}init();ld();setInterval(ld,300)</script></body></html>
function logout(){if(confirm('Logout?'))location.href='/logout'}
.html
.htm
//IDF/components/esp_hw_support/include/spinlock.h
/IDF/components/hal/esp32/include/hal/mwdt_ll.h
/IDF/components/hal/esp32/include/hal/mmu_ll.h
/IDF/components/hal/esp32/include/hal/clk_tree_ll.h
/IDF/components/hal/esp32/include/hal/timer_ll.h
```

> You can copy the HTML page and paste to any AI and request the AI to Make a complete reconstructed code function by function (followed by the code).
