# Coco Conjecture
The door to the next floor is guarded by a figure who calls herself "the dragon CEO". She does not speak of mercy or choice. only of order and efficiency.
To enter the next chamber, you must complete the task presented by her. Complete it exactly as instructed, achieving operational efficiency by her standards, and the path forward will open.

## How I solved
The description and transformations mentioned in Coco_Conjecture.pdf are self-explanatory. This mathematical problem is called Collatz Conjecture.
With the help of the pdf we can make a function that will calculate the collatz steps for each number returned by the server, and using helper.md which is provided along with the pdf, we can modify the script to communicate with the instance via socket or pwntools.
```
import socket
import re

def steps(n: int) -> int:
    s = 0
    while n != 1:
        if (n & 1) == 0:
            lb = n & -n
            z = lb.bit_length() - 1
            n >>= z
            s += z
        else:
            n = 3 * n + 1
            s += 1
    return s

with socket.create_connection(("127.0.0.1", 420)) as s:
    f = s.makefile("rwb", buffering=0) # turn socket into file object which makes certain operations faster
    while True:
        line = f.readline()
        if not line:
            break
        message = line.decode().strip()
        print(message) # print server data

        m = re.search(r"Round \d+: (\d+)", message)
        if m:
            n = int(m.group(1))
            ans = str(steps(n)) + "\n"
            f.write(ans.encode())
            
        elif "citadel{" in message:
            break # break if flag found in server ouput
```
Flag: `citadel{k1ryu_c0c0_h4s_4_g0_4t_4n_uns0lv3d_m4th3m4t1cs_pr0bl3m}`
