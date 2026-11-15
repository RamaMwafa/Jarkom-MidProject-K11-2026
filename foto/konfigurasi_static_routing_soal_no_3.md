## 1. R-PUSAT

```
enable
configure terminal
! Default route keluar ke R-ISP
ip route 0.0.0.0 0.0.0.0 203.0.113.45

! Static route ke LAN milik R-DC (via 10.88.241.34)
ip route 10.88.96.0 255.255.224.0 10.88.241.34
ip route 10.88.239.0 255.255.255.0 10.88.241.34

! Static route ke LAN milik R-UTARA (via 10.88.241.38)
ip route 10.88.0.0 255.255.192.0 10.88.241.38
ip route 10.88.236.0 255.255.254.0 10.88.241.38

! Static route ke LAN milik R-PELABUHAN (lewat R-UTARA 10.88.241.38)
ip route 10.88.160.0 255.255.224.0 10.88.241.38
ip route 10.88.240.0 255.255.255.128 10.88.241.38

! Static route ke LAN milik R-SELATAN (via 10.88.241.42)
ip route 10.88.64.0 255.255.224.0 10.88.241.42
ip route 10.88.240.128 255.255.255.128 10.88.241.42

! Static route ke LAN milik R-TIMUR (via 10.88.241.46)
ip route 10.88.128.0 255.255.224.0 10.88.241.46
ip route 10.88.232.0 255.255.252.0 10.88.241.46

! Static route ke LAN milik R-BARAT (via 10.88.241.50)
ip route 10.88.192.0 255.255.224.0 10.88.241.50
ip route 10.88.238.0 255.255.255.0 10.88.241.50
end
write memory
```

## 2. R-UTARA

```
enable
configure terminal
! Default route ke atas menuju R-PUSAT
ip route 0.0.0.0 0.0.0.0 10.88.241.37

! Static route ke bawah menuju LAN milik R-PELABUHAN (via 10.88.241.54)
ip route 10.88.160.0 255.255.224.0 10.88.241.54
ip route 10.88.240.0 255.255.255.128 10.88.241.54
end
write memory
```

## 3. R-PELABUHAN

```
enable
configure terminal
! Default route ke atas menuju R-UTARA
ip route 0.0.0.0 0.0.0.0 10.88.241.53
end
write memory
```

## 4. R-DC

```
enable
configure terminal
! Default route ke atas menuju R-PUSAT
ip route 0.0.0.0 0.0.0.0 10.88.241.33
end
write memory
```

## 5. R-SELATAN

```
enable
configure terminal
! Default route ke atas menuju R-PUSAT
ip route 0.0.0.0 0.0.0.0 10.88.241.41
end
write memory
```

## 6. R-TIMUR

```
enable
configure terminal
! Default route ke atas menuju R-PUSAT
ip route 0.0.0.0 0.0.0.0 10.88.241.45
end
write memory
```

## 7. R-BARAT

```
enable
configure terminal
! Default route ke atas menuju R-PUSAT
ip route 0.0.0.0 0.0.0.0 10.88.241.49
end
write memory
```
