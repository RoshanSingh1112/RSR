ttt=[[1,2,3],[4,5,6],[7,8,9]]
TTT=[[' ',' ',' '],[' ',' ',' '],[' ',' ',' ']]
row=[[1,2,3],[4,5,6],[7,8,9]]
col=[[7,4,1],[8,5,2],[9,6,3]]
diag=[[1,5,9],[3,5,7]]
t=[1,2,3,4,5,6,7,8,9]
U=[]
Sys=[]
count=0
def Uplay(n):
    global ttt
    global U
    global count
    global t
    U.append(n)
    for i in range(0,3):
        for j in range(0,3):
            if ttt[i][j]==n:
                ttt[i][j]='X'
                count=count+1
    check()
    Sysplay()
def Sysplay():
    global U
    global ttt
    global row
    global col
    global t
    if count<2:
        if ttt[1][1]=='X':
            Sys.append(ttt[0][1])
            ttt[0][1]='O'            
        else:
            Sys.append(ttt[1][1])
            ttt[1][1]='O'            
    else :
        m=0
        i=0
        while i<3:
            if len(set(Sys)&set(row[i]))==2 and len(set(U)&set(row[i]))==0:                
                        ele=list(set(row[i])-set(Sys))
                        m=ele[0]
                        Sys.append(m)
                        i=3
            elif len(set(Sys)&set(col[i]))==2 and len(set(U)&set(col[i]))==0:
                        ele=list(set(col[i])-set(Sys))
                        m=ele[0]
                        Sys.append(m)
                        i=3
            elif i<2 and len(set(Sys)&set(diag[i]))==2 and len(set(U)&set(diag[i]))==0:
                        ele=list(set(diag[i])-set(Sys))
                        m=ele[0]
                        Sys.append(m)
                        i=3
            elif len(set(U)&set(row[i]))==2 and len(set(Sys)&set(row[i]))==0:                
                        ele=list(set(row[i])-set(U))
                        m=ele[0]
                        Sys.append(m)
                        i=3
            elif len(set(U)&set(col[i]))==2 and len(set(Sys)&set(col[i]))==0:
                        ele=list(set(col[i])-set(U))
                        m=ele[0]
                        Sys.append(m)
                        i=3
            elif i<2 and len(set(U)&set(diag[i]))==2 and len(set(Sys)&set(diag[i]))==0:
                        ele=list(set(diag[i])-set(U))
                        m=ele[0]
                        Sys.append(m)
                        i=3
            elif i==2:
                L=U+Sys
                M=list(set(t)-set(L))
                m=M[0]
                Sys.append(m)
                i=3
            else :
                i=i+1       
        for i in range(0,3):
            for j in range(0,3):
                if ttt[i][j]==m:
                    ttt[i][j]='O'
    disp()
    check()
    n=int(input('enter position :'))
    Uplay(n)
def check():
    global ttt
    global row
    cout=0
    tc=[[ttt[0][0],ttt[1][0],ttt[2][0]],[ttt[0][2],ttt[1][2],ttt[2][2]],[ttt[0][1],ttt[1][1],ttt[2][1]]]
    td=[[ttt[0][0],ttt[1][1],ttt[2][2]],[ttt[0][2],ttt[1][1],ttt[2][0]]]
    for i in range(0,3):
        if ttt[i]==['X','X','X']:
            print('you win ')
            disp()
            exit(0)        
        elif ttt[i]==['O','O','O']:
            print('you lose ')
            disp()
            exit(0)
        elif tc[i]==['X','X','X']:
            print('you win ')
            disp()
            exit()
        elif tc[i]==['O','O','O']:
            print('you lose ')
            disp()
            exit()
    for i in range(0,2):
        if td[i]==['X','X','X']:
            print('you win ')
            disp()
            exit(0)
        elif td[i]==['O','O','O']:
            print('you lose ')
            disp()
            exit(0)
    for i in range(0,3):
        if len(set(row[i])&set(ttt[i]))==0:
            cout=cout+1
    if cout==3:
        print('Match drow , Try again :')
        disp()
        exit(0)   
def disp():
    global ttt
    global TTT
    for i in range(0,3):
        for j in range(0,3):
            if ttt[i][j]=='X':
                TTT[i][j]='X'
            if ttt[i][j]=='O':
                TTT[i][j]='O'
    a=''
    p=0
    q=0
    for i in range(0,5) :
        if i%2 is 0:
            for j in range (0,5):
                if  j%2==0  and q<3:
                    a=a+str(TTT[p][q])
                    q=q+1
                elif  not j%2== 0:
                    a=a+'|'
            p=p+1
            q=0
        
        elif i%2 != 0:
            for j in range (0,5):
                if  j%2==0:
                    a=a+'-'
                    
                elif j%2!=0:
                    a=a+' '
            
        print(a,'\n',end='')
        a=''                        
disp()            
play=Uplay(int(input('enter position : ')))        
        
    
    
    
