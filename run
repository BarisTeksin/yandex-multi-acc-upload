from YaDiskClient.YaDiskClient import YaDisk
import os
import sys

f_accounts = open('acc.txt','r')
acc_arr = [account for account in f_accounts]
f_accounts.close()
files_arr = os.listdir('.')
f_urls = open('urls.txt','w')
for files in files_arr:
    for account in acc_arr:
        email = account.split(':')[0]
        password = account.replace('\n','').split(':')[1]
        disk = YaDisk(email, password)
        disk.df()
        if files == 'urls.txt' or files == os.path.basename(__file__) or files == 'acc.txt':
            continue
        print(os.path.join(os.path.dirname(os.path.abspath(__file__)),files) + ' ---> ' + files)
        disk.upload(os.path.join(os.path.dirname(os.path.abspath(__file__)),files), files)
        shared_url = disk.publish('/' + files)
        f_urls.write('{} -->  Filename : {} -->  Shared Url : {}\n'.format(email,files,shared_url))
f_urls.close()
sys.exit()
