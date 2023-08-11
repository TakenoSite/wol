# wol



    $macAddress=[byte[]]("2C:F0:5D:57:18:7C".Split(":")|%{ [Convert]::ToInt32($_, 16)}) #富士通PC有線LAN　NIC
    $header=[byte[]](@(0xFF)*6)
    $magicpacket = $header + $macAddress * 16 
    $client=new-object System.Net.Sockets.UdpClient
    $target=[System.Net.IPAddress]::Parse("192.168.2.255")  #対象セグメントブロードキャストアドレス
    $client.Connect($target,2304)
    $client.Send($magicPacket,$magicPacket.Length)
    $client.Close() 

    04-6C-59-0C-32-8A
    192.168.2.126


    
