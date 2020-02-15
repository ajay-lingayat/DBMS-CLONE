import os
import shutil


def dbms():
    print("***"*33)
    print()
    print('\t\t\t                    DBMS')
    print()
    print('***'*33)
    print()
    sq()
    
def sq():
    database2=[0]
    while True:
          a=input('<<< ').strip()
          b=a.upper()
          if b[:16]=='CREATE DATABASE ' and a[-1]=='.':
             if '_' in a[16:-1] or '_' not in a[16:-1]:
                c=a[16:-1].replace('_','')
                if c.isalnum()==True:
                   if not os.path.exists(a[16:-1]):
                      os.mkdir(a[16:-1])
                      print('Querry ok.\nDatabase Successfully Created....')
                      print()
                   elif os.path.exists(a[16:-1]):
                        print(f'{a[16:-1]} Database Exists....')
                        print()
          elif b=='CREATE DATABASE.':
               print(f'ERR0R : {a}\nLine No-->1\n!!!!>Database Name is not Given....')
               print()
          elif b[:4]=='USE ' and a[4:-1].isalnum()==True and b[-1]=='.':
               if os.path.exists(a[4:-1]):
                  database2.append(a[4:-1])
                  print('Querry ok.\nDatabase Changed Successfully....')
                  print()
               elif not os.path.exists(a[4:-1]):
                    print(f"ERROR : {a}\nline No-->1\n!!!!>Database {a[4:-1]} Doesn't Exists....")
                    print()
         #Create Table
          elif b[:13]=='CREATE TABLE ' and (a[13:].isalnum()==True or (a[13:].isalnum()==True and '-' in a[13:-1])) and database2[-1]!=0:
               if not os.path.exists(f'{database2[-1]}\{a[13:]}'):
                  d=[]
                  d1=[]
                  while True:
                        k=input('--->').strip()
                        if k[-1]=='.' and len(k)!=0:
                           break
                        else:
                           d.append(k)
                  for e in d:
                      h=e.upper()
                      if h[-1]==',' and ' ' in h and h.count(' ')==1 and h[:h.find(' ')].replace('_','').isalnum()==True:
                         if h[h.find(' ')+1:-1]=='INT' or h[h.find(' ')+1:-1]=='CHAR':
                            d1.append(e)
                      else:
                         print(f'ERROR : {a}\nLine No-->1\n!!!!>Invalid Querry....')
                         print()
                         break
                  if len(d)==len(d1):
                     d3=1
                     os.mkdir(database2[-1]+'/'+a[13:])
                     for kl in d1:
                         with open(f'{database2[-1]}/{a[13:]}/{d3}{kl}.txt','w') as w:
                              w.write('Data:')
                         w.close()
                         d3+=1
                     print('Table Created successfully....')
                  #Database Exists    
               elif os.path.exists(f'{database2[-1]}\{a[13:]}'):
                   print(f'ERROR : {a}\nline No-->1\n!!!!>{a[13:]} Table already Exists....')
                   print()

          
          elif b[:13]=='CREATE TABLE ' and a[13:].isalnum()==True and database2[-1]==0:
               print(f'ERROR : {a}\nline No-->1\n!!!!>No Database is Used....')
               print()
          elif b=='SHOW DATABASES.':
               print('-'*33)
               print('!          DATABASES            !')
               print('-'*33)
               an=os.listdir()
               list1=[]
               for e in an:
                   list1.append(e)
               for k in list1:
                   if k!='DBMS_CLONE.py' and k!='dbms1.py' and k!='__pycache__':
                      print(F'! {k}'+(' '*((33-len(k))-3))+'!')
               print('-'*33)
               print()
          elif b=='SHOW TABLES.':
               if database2[-1]!=0:
                  print('-'*33)
                  print('!          TABLES               !')
                  print('-'*33)
                  an=os.listdir(f'{database2[-1]}')
                  list1=[]
                  for e in an:
                      list1.append(e)
                  for k in list1:
                      print(F'! {k}'+(' '*((33-len(k))-3))+'!')
                  print('-'*33)
                  print()
               else:
                   print(f'ERROR : {a}\nline No-->1\n!!!!>No Database is Used....')
                   print()
          elif b[:4]=='DEL ' and b[-1]=='.' and b[4:-1].isalnum()==True:
               if os.path.exists(f'{b[4:-1]}'):
                  shutil.rmtree(f'{b[4:-1]}')
                  print('Database Deleted Successfully....')
                  print()
               else:
                  print(f"ERROR : {a}\nLine No-->1\n!!!!>Database {b[4:-1]} Doesn't Exists....")
                  print()
          elif b[:10]=='DEL TABLE ' and b[-1]=='.' and b[10:-1].isalnum()==True and database2[-1]!=0:
               if os.path.exists(f'{database2[-1]}/{b[10:-1]}'):
                  shutil.rmtree(f'{database2[-1]}/{b[10:-1]}')
                  print('Table Deleted Successfully....')
                  print()
               else:
                  print(f"ERROR : {a}\nLine No-->1\n!!!!>Table {b[10:-1]} Doesn't Exists....")
                  print()
          elif b[:10]=='DEL TABLE ' and b[-1]=='.' and b[10:-1].isalnum()==True and database2[-1]==0:
               print(f'ERROR : {a}\nline No-->1\n!!!!>No Database is Used....')
               print()
          elif b[:9]=='ADD INTO ' and a[9:].isalnum()==True and database2[-1]!=0:
               if os.path.exists(f'{database2[-1]}/{a[9:]}'):
                  x=os.listdir(f'{database2[-1]}/{a[9:]}')
                  d1=[]
                  d2=[]
                  k=0
                  while True:
                        if k==len(x):
                           break
                        else:
                           eg=input('-->')
                           d1.append(eg)
                           k+=1
                  for i in range(0,len(x)):
                      if x[i].upper().endswith(' CHAR,.TXT'):
                         d2.append(str(d1[i]))
                      elif x[i].upper().endswith(' INT,.TXT'):
                           if d1[i].isdigit()==True:
                              d2.append(int(d1[i]))
                           elif d1[i].isdigit()==False:
                                print(f'ERROR : {d1[i]}\nLine No-->{d1.index(d1[i])+1}\n!!!!>The Data Type of the Column {x[i][:-5]} should be Integer Value.')
                                break
                  if len(x)==len(d2):
                     for k in range(0,len(x)):
                         with open(f'{database2[-1]}/{a[9:]}/{x[k]}','a') as out:
                              out.write(f'\n{d2[k]}')
                         out.close()
                     print(f'Data Added To The Table {a[9:]} successfully....')
                     print()
               elif not os.path.exists(f'{database2[-1]}\{a[9:]}') and database2[-1]!=0:
                    print(f"ERROR : Table {a[9:]} Doesn't Exists....")
                    print()
               elif b[:9]=='ADD INTO ' and b[9:].isalnum()==True and database2[-1]==0:
                    print(f'ERROR : {a}\nline No-->1\n!!!!>No Database is Used....')
                    print()
          elif b[:14]=='SELECT * FROM ' and b[-1]=='.' and database2[-1]!=0 and b[14:-1].isalnum()==True:
               if os.path.exists(f'{database2[-1]}/{a[14:-1]}'):
                  x=os.listdir(f'{database2[-1]}/{a[14:-1]}')
                  print()
                  print(x)
                  print()
                  x1=[]
                  files=open(f'{database2[-1]}/{a[14:-1]}/{x[0]}','r')
                  for each in files:
                      x1.append((str(each).replace('\n','')))
                  print(x1)
                  lm=''
                  for kl in range(1,len(x1)):
                      lm+={x[kl-1]}/{x1[kl]}
                      print(lm)
##                  print(x)
##                  x1=[]
##                  x2=[]
##                  for z in x:
##                      if z[0].isdigit()==True:
##                         z1=z.find(' ')
##                         x1.append(z[0+1:])
##                         x2.append(z[0+1:z1])
##                      elif z[:2].isdigit()==True:
##                         z1=z.find(' ')
##                         x1.append(z[0+1:])
##                         x2.append(z[1+1:z1])
##                  print(x1)
                  
               elif not os.path.exists(f'{database2[-1]}/{a[14:-1]}'):
                    print(f"ERROR : Table {a[9:]} Doesn't Exists....")
          elif b[:14]=='SELECT * FROM ' and b[-1]=='.' and database2[-1]==0 and b[14:-1].isalnum()==True:
               print(f'ERROR : {a}\nline No-->1\n!!!!>No Database is Used....')
               print()

          else:
              print(f'ERROR : {a}\nLine No-->1\n!!!!>Invalid Querry....')
              print()
dbms()
