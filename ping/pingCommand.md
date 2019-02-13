Ping 指令
==========================
~~~
    -t             Ping 指定的主機，直到停止。
                   若要查看統計資料並繼續，請按 Control-Break;
                   若要停止，請按 Control-C。
    -a             將位址解析為主機名稱。
    -n count       要傳送的回應要求數目。
    -l size        傳送緩衝區大小。
    -f             在封包中設定 Don't Fragment 旗標 (僅 IPv4)。
    -i TTL         存留時間。
    -v TOS         服務類型 (僅 IPv4。此設定已過時，而且對 IP 標頭中的
                   服務類型欄位沒有影響)。
    -r count       記錄路由以供計算躍點 (僅 IPv4)。
    -s count       供計算躍點的時間戳記 (僅 IPv4)。
    -j host-list   鬆散的主機清單的來源路由 (僅 IPv4)。
    -k host-list   嚴格的主機清單來源路由 (僅 IPv4)。
    -w timeout     每個回覆的等候逾時 (單位為毫秒)。
    -R             也使用路由標頭測試反向路由 (僅 IPv6)。
                   根據 RFC 5095，已不再使用此路由標頭。如果使用此標頭，某些
                   系統可能會捨棄回應要求。
    -S srcaddr     要使用的來源位址。
    -c compartment 路由區間識別碼。
    -p             對 Hyper-V 網路虛擬化提供者位址執行 Ping。
    -4             強制使用 IPv4。
    -6             強制使用 IPv6。
~~~

1. ping -t -l {buffer size} {ip}
> ping -t -l 20488 10.11.1.188


2. 可寫成 Scripts:
~~~batch 
@echo off

@pause  
~~~ 