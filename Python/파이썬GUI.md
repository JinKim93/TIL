# 파이썬 GUI

## Tkinter
- Tkinter는 최신 Python 프로그램에 포함된 내장된 모듈
- Tcl/Tk에 대한 파이썬 Wrapper
- Tcl : Tool Command Language 일종의 프로그래밍 언어
- Tk : Took kit 일종의 GUI 툴킷
- 지원되는 위젯들이 부족하고 UI도 예쁘지는 않지만, 간단히 GUI 만들 떄 쉽게 사용
- **파이참 Pyqt5 사용하면 GUI 이쁘게 가능**

## Tkinter의 기본 문장
### Tkinter 모듈 import
```py
from tkinter import *

root = Tk() # root = new Tk(), root 객체 생성,  Tk() -> 윈도우 만들어주는 역할
root.mainloop() # root는 윈도우, mainloop 돌게끔 설정

```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166200466-11d95e03-b6ce-4725-b35a-5fffdf423fa6.png)

### 타이틀 생성
```py
from tkinter import *

root = Tk() 
root.title("Python GUI")

root.mainloop() 
```
### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166200718-194fd414-6c13-4a56-97a9-d967f677dcbf.png)


### 윈도우 창 일정크기로 설정
```py
from tkinter import *

root = Tk() 
root.title("Python GUI")
root.geometry('800x600+200+100') #크기 800x600,  200 x축, 100 y축 -> 실행시 특정위치에 고정되서 나오게 해줌
root.resizable(False,False) # 윈도우 x,y 사이즈 조절 못하게 false로 막음 True로 하면 변경 가능
root.mainloop() 

```

### 출력결과
- 사이즈 800 x 600으로 고정되어 출력

![image](https://user-images.githubusercontent.com/82345970/166200947-8230439e-de6b-466c-9e27-994083f46b9a.png)

### 위젯이란
- 버튼,체크박스,리스트박스,라디오버튼,슬라이드바, 텍스트, 메뉴바, 프로그레스바 등 의 컨트롤들을 통틀어 **위젯** 이라고 함

### 버튼 만들기
- Button() 위젯을 사용

```py
from tkinter import *

root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')

btn1 = Button(root,text = "버튼인가?") # btn1 = new Button()
btn1.pack() # pack() 없으면 안된다.

root.mainloop() 
```

### 출력결과
- pack()을 해야만 실제 루트에 버튼이 포함된다.
 
![image](https://user-images.githubusercontent.com/82345970/166202113-0a924c8b-e74a-4de8-8d24-d3b562f681bd.png)

### 버튼 출력
```py
from tkinter import *

root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')

btn1 = Button(root, text = "나버튼인가?") # btn1 = new Button()
btn1.pack()


btn2 = Button(root, padx = 20, pady = 50, text = "아무튼")
btn2.pack()

btn3 = Button(root,width = 10, height = 5, text = "튼튼", fg = "white", bg = "red")
btn3.pack()

root.mainloop() 




```

### 출력결과
- 빨간색배경, 흰색 글씨

![image](https://user-images.githubusercontent.com/82345970/166205283-e3627744-91b3-4e46-9f3c-efacd436bcaa.png)


### 버튼 이미지 넣기, 버튼 눌렀을때 이벤트
```py
from tkinter import *


root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')

def btncmd():
    print("좋아요를 꾸~욱 눌러주세요")

photo = PhotoImage(file = "jamsuham.png")
btn = Button(root, image = photo, command= btncmd)
btn.pack()

root.mainloop() 

```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166206699-1202d3fe-0318-4f7c-8db2-25f997a778fe.png)

### 레이블 예제
```py
from tkinter import *


root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')

label = Label(root, text = "누구인가?")
label.pack()

root.mainloop() 
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166207516-2d742c3b-81dd-4001-adba-3c8c4c603a9b.png)

### 레이블 이미지 넣기
```py
from tkinter import *


root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')

photo = PhotoImage(file = "jamsuham.png")
label = Label(root, image=photo)
label.pack()

root.mainloop() 
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166207653-904b9656-f2cd-4d7a-af01-fc9b5b6ab395.png)


### 버튼,레이블 조합 예제
```py
from tkinter import *


root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')


label = Label(root, text = "최선을 다하자")
label.pack()

def change():
    label.config(text = "아자아자 화이팅") # config -> label text 변경해준다
btn = Button(root, text = "클릭", command = change)
btn.pack()
root.mainloop() 
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166208317-48d06562-7dec-44e9-ba74-b9ece16c83ce.png)


### 버튼 클릭시, 이미지 변경
```py
from tkinter import *


root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')


label = Label(root, text = "최선을 다하자")
label.pack()

def change():
    global photo #photo 전역변수로 만들어줌, 지역변수로 하면, 클릭시 지역변수라서 유지가 안됨
    photo = PhotoImage(file = "jamsuham.png")
    label.config(image=photo)
btn = Button(root, text = "클릭", command = change)
btn.pack()
root.mainloop() 
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166208793-9eaa3fe0-1765-40e5-96bd-af7ff44d71dd.png)

### TEXT 입력창 만들기
```py
from tkinter import *


root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')

txt = Text(root, width = 40, height = 20)
txt.pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166637991-93cb297a-680a-4e71-aabb-603757f9647c.png)

### TEXT 입력창 만들기
- **입력창에 미리 글자 입력하는 방법**

```py
from tkinter import *


root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')

txt = Text(root, width = 40, height = 20)
txt.insert(END, "글자를 입력하세요")
txt.pack()

root.mainloop()
```
### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166638197-824b88b5-3a15-4858-9a32-35274e9260e9.png)

### Entry를 이용한 로그인창 만들기
```py
from tkinter import *


root = Tk() 
root.title("Python Button")
root.geometry('800x600+200+100')

ent1 = Entry(root, width = 30)
ent1.insert(END, "ID를 입력하세요")
ent1.pack()

ent2 = Entry(root, width = 30)
ent2.insert(END, "비밀번호를 입력하세요")
ent2.pack()

def btncmd():
    print(ent1.get())
    print(ent2.get())

def btndelete():
    ent1.delete(0,END)
    ent2.delete(0,END)
btn = Button(root, text = "로그인", command = btncmd)
btn.pack()

btn2 = Button(root, text = "삭제", command = btndelete)
btn2.pack()

root.mainloop()

```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166639990-aa5567d5-70ee-4035-a809-a39e2bd6e9ad.png)

### Listbox 예제
```py
from tkinter import *


root = Tk() 
root.title("Python listbox")
root.geometry('800x600+200+100')

listbox = Listbox(root,selectmode = "extended", height = 5)

listbox.insert(0, "파이썬")
listbox.insert(1, "C#")
listbox.insert(2, "HTML5")

listbox.insert(END, "자바")
listbox.insert(END, "Node")
listbox.pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166640731-b453787d-2269-487e-8bbb-209afecc6f1a.png)

### Listbox 예제
- **selectmode = single로 바꾸면 리스트에 있는 항목들 shift(키보드)눌렀을때 여러항목 선택 안 됨**
- **height =10 리스트항목 10개 생김**
```py
from tkinter import *


root = Tk() 
root.title("Python listbox")
root.geometry('800x600+200+100')

listbox = Listbox(root,selectmode = "single", height = 10) 

listbox.insert(0, "파이썬")
listbox.insert(1, "C#")
listbox.insert(2, "HTML5")

listbox.insert(END, "자바")
listbox.insert(END, "Node")
listbox.pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166641386-76cded3e-89eb-4e11-93ab-a80fc27cbba7.png)


### 리스트 삭제
```py
from tkinter import *


root = Tk() 
root.title("Python listbox")
root.geometry('800x600+200+100')

listbox = Listbox(root,selectmode = "single", height = 10) 

listbox.insert(0, "파이썬")
listbox.insert(1, "C#")
listbox.insert(2, "HTML5")

listbox.insert(END, "자바")
listbox.insert(END, "Node")
listbox.pack()

def btncmd():
    listbox.delete(END)

btn = Button(root, text = "삭제", command = btncmd)
btn.pack()

root.mainloop()
```

### 리스트 -> 튜플형태로 가져오기
```py
from tkinter import *


root = Tk() 
root.title("Python listbox")
root.geometry('800x600+200+100')

listbox = Listbox(root,selectmode = "single", height = 10) 

listbox.insert(0, "파이썬")
listbox.insert(1, "C#")
listbox.insert(2, "HTML5")

listbox.insert(END, "자바")
listbox.insert(END, "Node")
listbox.pack()

def btncmd():
    listbox.delete(END)

def btnfetch():
    print(listbox.get(0,2)) # 튜플형태로 가져온다


btn = Button(root, text = "삭제", command = btncmd)
btn.pack()

btn = Button(root, text = "가져오기", command = btnfetch)
btn.pack()

root.mainloop()
```

### 출력결과
- 0부터 2까지 리스트박스항목, 튜플로 가져옴

![image](https://user-images.githubusercontent.com/82345970/166644012-037467b4-8980-42ed-ad26-50166b6f43a9.png)

### 리스트박스 선택한 항목 및 개수 구하기
```py
from tkinter import *


root = Tk() 
root.title("Python listbox")
root.geometry('800x600+200+100')

listbox = Listbox(root,selectmode = "extended", height = 10) 

listbox.insert(0, "파이썬")
listbox.insert(1, "C#")
listbox.insert(2, "HTML5")

listbox.insert(END, "자바")
listbox.insert(END, "Node")
listbox.pack()

def btncmd():
    listbox.delete(END)

def btnfetch():
    print(listbox.get(0,2)) # 튜플형태로 가져온다


def btnselect():
    print("선택한 항목 : ", listbox.curselection())
    print('항목개수 : ', listbox.size())
btn = Button(root, text = "삭제", command = btncmd)
btn.pack()

btn = Button(root, text = "가져오기", command = btnfetch)
btn.pack()

btn = Button(root, text = "선택항목", command = btnselect)
btn.pack()


root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166644432-87f2a075-79ba-413f-8255-28f2c9a4cc66.png)

### 체크박스 위젯
```py
from tkinter import *


root = Tk() 
root.title("Python listbox")
root.geometry('800x600+200+100')

chkclick = IntVar()
chkbox = Checkbutton(root, text = "오늘 하루 그만 보기", variable = chkclick)
chkbox.pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166644943-9be86a73-8d67-4ab4-aa83-fb784329a793.png)

### 체크박스 체크확인 하기
```py
from tkinter import *


root = Tk() 
root.title("Python listbox")
root.geometry('800x600+200+100')

chkclick = IntVar()
chkbox = Checkbutton(root, text = "오늘 하루 그만 보기", variable = chkclick)
chkbox.pack()

def btncmd():
    print("체크 상태 : ", chkclick.get())

btn = Button(root, text = "확인", command = btncmd)
btn.pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166645391-b9be2e9d-7a67-49b7-a25f-ed7ee173181b.png)


### 햄버거를 선택하세요 
```py
from tkinter import *

root = Tk()
root.title('Python listBox')
root.geometry('800x600+200+100')

Label(root, text="햄버거를 선택하세요").pack()

burger_var = StringVar() #객체생성
btn_burger1 = Radiobutton(root, text="불고기버거", value="불고기버거", variable=burger_var)
btn_burger1.select() #선택되어있는 Radiobutton
btn_burger2 = Radiobutton(root, text="치즈버거", value="치즈버거", variable=burger_var)
btn_burger3 = Radiobutton(root, text="새우버거", value="새우버거", variable=burger_var)

btn_burger1.pack()
btn_burger2.pack()
btn_burger3.pack()

def btncmd():
    print(burger_var.get() + '를 선택하셨습니다.')
btn=Button(root, text="주문", command=btncmd)
btn.pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/166648576-641540ba-54ea-4f14-9d2c-613c412b805f.png)

### 콤보박스 만들기
- 콤보박스는 모듈이 다른 곳에 있어 모듈 선언을 해주어야 한다.
- import tkinter.ttk as ttk
- height : 콤보박스를 클릭했을 때 화면에 나오는 목록 개수(height = 5 지정하면 5개가 기본으로 화면에 보임)
- width : 콤보박스 너비 설정
- values : 콤보 박스 내에 어떤 값을 넣을지 정의
- coobobox.set() : 최초 목록 제목을 설정할 때, 값 설정할때 사용

### 콤보박스 예제
```py
import tkinter. ttk as ttk
from tkinter import *

root = Tk()
root.title("GUI Test")
root.geometry("600x400")

dateVal = [str(i) + "일" for i in range(1,32)] # 1부터 31까지 숫자
combobox = ttk.Combobox(root, height = 5, values = dateVal, state = "readonly")
combobox.current(0)
combobox.pack()
combobox.set("통장은거들뿐")

def btncmd():
    print(combobox.get())

btn = Button(root, text = "Select", command = btncmd)
btn.pack()

root.mainloop()


```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/167353427-8829ac9e-b2e5-4e83-ad19-952a92bb0e52.png)



### 진행표시줄(ProgressBar)
```py
import tkinter. ttk as ttk
from tkinter import *

root = Tk()
root.title("GUI Test")
root.geometry("600x400")

progressbar1 = ttk.Progressbar(root, maximum = 100, mode = "indeterminate")
progressbar1.pack()

progressbar2 = ttk.Progressbar(root, maximum = 100, mode = "determinate")
progressbar2.pack()

def btnStart():
    progressbar1.start(10);
    progressbar2.start(10);

btn1 = Button(root, text = "start", command = btnStart)
btn1.pack()

def btnStop():
    progressbar1.stop();
    progressbar2.stop();

btn2 = Button(root, text = "stop", command = btnStop)
btn2.pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/167355320-d1b376a6-18c9-47b0-a7c1-b2d80218df2d.png)


### send progress
```py
import time
import tkinter. ttk as ttk
from tkinter import *

root = Tk()
root.title("GUI Test")
root.geometry("600x400")

p_var = DoubleVar()
progressbar1 = ttk.Progressbar(root, maximum = 100, length = 200, variable = p_var)
progressbar1.pack()



def btnStart():
    for i in range(1, 101):
        time.sleep(0.01)
        p_var.set(i)
        progressbar1.update()
        print(p_var.get())
              

btn1 = Button(root, text = "send", command = btnStart)
btn1.pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/167357203-534ef186-70e6-4896-9f51-56ae51423918.png)

### 메뉴 만들기
- **기본 틀에 메뉴선언**
  - mymenu = Menu(root)
  - root.config(menu = mymenu)

- **File 메뉴에 서브메뉴 New File 삽입**
  - add_cascade() : File 메뉴에 포함된 모든 서브 메뉴를 연결하는 기능

### 메뉴만들기 실습
```py
import time
import tkinter. ttk as ttk
from tkinter import *

root = Tk()
root.title("GUI Test")
root.geometry("600x400")

def btncmd():
    print("New File")

mymenu = Menu(root)
menu_file = Menu(mymenu, tearoff = 0)
menu_file.add_command(label = "New File", command = btncmd)
menu_file.add_command(label = "New Window")
menu_file.add_separator()
menu_file.add_command(label = "Open File")
menu_file.add_separator()
menu_file.add_command(label = "Save All")
menu_file.add_separator()
menu_file.add_command(label = "Exit", command = root.destroy)
mymenu.add_cascade(label = "File", menu = menu_file)


mymenu.add_cascade(label = "Edit")

menu_view = Menu(mymenu, tearoff = 0)
menu_view.add_checkbutton(label = "show minimap")
menu_view.add_checkbutton(label = "show maxmap")
mymenu.add_cascade(label = "view", menu = menu_view)

root.config(menu = mymenu)

Button(root, text = "Quit", command = root.destroy).pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/167364634-18e3cad5-f37a-4282-80a6-0f800c72381d.png)

### 메시지 박스
```py
import time
import tkinter. ttk as ttk
from tkinter import *
import tkinter .messagebox as msgbox

root = Tk()
root.title("GUI Test")
root.geometry("600x400")

def info():
    msgbox.showinfo("알림", "정상적으로 예매 완료되었습니다.")

Button(root, command = info, text = "알림").pack()


root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/167365636-eb22932b-66b7-4fcb-9de7-a216c3ac7f46.png)

### 메시지 박스(알림,경고,에러)
```py
import time
import tkinter. ttk as ttk
from tkinter import *
import tkinter .messagebox as msgbox

root = Tk()
root.title("GUI Test")
root.geometry("600x400")

def info():
    msgbox.showinfo("알림", "정상적으로 예매 완료되었습니다.")
    
def warn():
    msgbox.showwarning("경고", "해당 좌석은 매진되었습니다")

def error():
    msgbox.showerror("에러", "결재 오류가 발생했습니다.")

Button(root, command = info, text = "알림").pack()
Button(root, command = warn, text = "경고").pack()
Button(root, command = error, text = "에러").pack()


root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/167366725-e341e2d4-446a-423d-a3be-4a9b939febf0.png)


### 메시지 박스(확인/취소)
```py
import time
import tkinter. ttk as ttk
from tkinter import *
import tkinter .messagebox as msgbox

root = Tk()
root.title("GUI Test")
root.geometry("600x400")

def info():
    msgbox.showinfo("알림", "정상적으로 예매 완료되었습니다.")
    
def warn():
    msgbox.showwarning("경고", "해당 좌석은 매진되었습니다")

def error():
    msgbox.showerror("에러", "결재 오류가 발생했습니다.")

def okcancel():
    res = msgbox.askokcancel("확인/취소", "해당 좌석은 유아동반석입니다. 예매하시겠습니까?")
    if res == 1:
        print("예")
    elif res == 0:
        print("아니오")
    else:
        print("취소")        

Button(root, command = info, text = "알림").pack()
Button(root, command = warn, text = "경고").pack()
Button(root, command = error, text = "에러").pack()
Button(root, command = okcancel, text = "확인/취소").pack()

root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/167367566-e25e18ae-0776-49dd-8c2b-d9fdb5e8c78e.png)

### 그리드
- 격자인데 보통 바둑판에 비유되고, 바둑판 격자 하나하나에 삽입될 다양한 것들을 디자인할 때 유용하게 사용

![image](https://user-images.githubusercontent.com/82345970/167370319-2790f7ea-c2a5-401f-8b6e-2f402c85245b.png)

### 그리드 pack과 grid를 적용한 버튼 실행결과 비교
- 그리드는 위치를 지정해서 원하는 버튼을 넣을 수 있는 장점이 있다

![image](https://user-images.githubusercontent.com/82345970/167370521-24a17e7e-545d-470f-a96e-6497eee98740.png)


### 그리드 실습
```py
import time
import tkinter. ttk as ttk
from tkinter import *

root = Tk()
root.title("GUI Test")
root.geometry("600x400")

Button(root, text = "F16", width = 8, height = 2).grid(row = 0, column = 0, sticky = N + E + W + S, padx = 3, pady =3) 
Button(root, text = "F17", width = 8, height = 2).grid(row = 0, column = 1, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "F18", width = 8, height = 2).grid(row = 0, column = 2, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "F19", width = 8, height = 2).grid(row = 0, column = 3, sticky = N + E + W + S, padx = 3, pady =3)

Button(root, text = "clear", width = 8, height = 2).grid(row = 1, column = 0, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "=", width = 8, height = 2).grid(row = 1, column = 1, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "/", width = 8, height = 2).grid(row = 1, column = 2, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "*", width = 8, height = 2).grid(row = 1, column = 3, sticky = N + E + W + S, padx = 3, pady =3)

Button(root, text = "7", width = 8, height = 2).grid(row = 2, column = 0, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "8", width = 8, height = 2).grid(row = 2, column = 1, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "9", width = 8, height = 2).grid(row = 2, column = 2, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "-", width = 8, height = 2).grid(row = 2, column = 3, sticky = N + E + W + S, padx = 3, pady =3)

Button(root, text = "4", width = 8, height = 2).grid(row = 3, column = 0, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "5", width = 8, height = 2).grid(row = 3, column = 1, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "6", width = 8, height = 2).grid(row = 3, column = 2, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "+", width = 8, height = 2).grid(row = 3, column = 3, sticky = N + E + W + S, padx = 3, pady =3)

Button(root, text = "1", width = 8, height = 2).grid(row = 4, column = 0, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "2", width = 8, height = 2).grid(row = 4, column = 1, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "3", width = 8, height = 2).grid(row = 4, column = 2, sticky = N + E + W + S, padx = 3, pady =3)
Button(root, text = "enter", width = 8, height = 2).grid(row = 4, column = 3, sticky = N + E + W + S, padx = 3, pady =3)


root.mainloop()
```

### 출력결과
![image](https://user-images.githubusercontent.com/82345970/167373997-6a91d636-2a0b-4d0c-a31c-94248075b4d7.png)
