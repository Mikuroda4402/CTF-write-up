#python 2.7
import sys, hashlib, socket
s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
s.connect(('255.255.255.255', 65535))

count = 0
while count < 6:
    count += 1
    data = s.recv(1024)
    print data
    if count == 1:
        data = data.split('\'')[1]
        print 'x[:6] = ' + data
        tmp = ''
        z = '0123456789ABCDEFGHIJKLMNOPQRSTUVWXYZ'
        pof_count = 0
        print 'Proof of work - searching...'
        while ( tmp[:6] != '000000'):
            pof_count += 1
            y = ''
            tmp = pof_count
            while ( tmp > 36 ):
                y = z[(tmp % 36) -1] + y
                tmp /= 36
            y = z[tmp -1] + y
            tmp = hashlib.sha256( data + y ).hexdigest()
        data = data + y + "\n"
        print data
        s.send(data)
        data = s.recv(1024)
        print data
        break
    print 'dis_message ' + str(count) + ' end.'
