```c
#include <iostream>
using namespace std;

class Phone
{
private:
	int num;
	int shape;
	const char* sms;
public:
	Phone() {}
	Phone(const char* msg)
	{
		sms = msg;
	}
	~Phone() {}
	const char* Receive() const { return sms; }
	void Call() {}
	void Send(const char* msg)
	{
		sms = msg;
	}
};

void main()
{
	
	Phone ph("분리수거를 잘하자");
	Phone* pObj;
	pObj = &ph;
	std::cout << pObj->Receive();



	
}

```



```c
#include <iostream>
using namespace std;

class Phone
{
private:
	int num;
	int shape;
	const char* msg;
public:
	Phone() {}
	Phone(const char* msg)
	{
		this->msg = msg;
	}
	~Phone() {}
	const char* Receive() const { return this->msg; }
	void Call() {}
	void Send(const char* msg)
	{
		this->msg = msg;
	}
};

void main()
{
	
	Phone ph("분리수거를 잘하자");
	Phone* pObj;
	pObj = &ph;
	std::cout << pObj->Receive();



	
}
```

### 힙영역 메모리 할당

```c
#include <iostream>
using namespace std;

void main()
{
	
	int* pBuffer;
	int nLength;
	
	cin >> nLength;

	pBuffer = new int[nLength];
	



	delete[] pBuffer;


	
}
```

### 동적메모리 할당

```c
#include <iostream>
using namespace std;

void main()
{
	
	int* pBuffer;
	int nLength;
	
	cin >> nLength;
	pBuffer = new int[nLength];

	for (int i = 0; i < nLength; i++)
	{
		pBuffer[i] = i + 1;
	}

	for (int i = 0; i < nLength; i++)
	{
		cout << pBuffer[i] << " ";

	}
		
	delete[] pBuffer;


	
}
```

```c
#include <iostream>
using namespace std;
class MousePoint
{
public:
	MousePoint();
	MousePoint(int nX, int nY);
	void SetXY(int X, int Y);
	int GetX()
	{ 
	 return x; 
 	};
	int GetY() 
	{ 
		return y;
	};
private:
	int x, y;
};
MousePoint::MousePoint() {
}
MousePoint::MousePoint(int nX, int nY) {
	x = nX;
	y = nY;
}

void main()
{
	MousePoint* pt;
	pt = new MousePoint(100, 200);
	cout << pt->GetX() << endl;
	cout << pt->GetY() << endl;
	delete pt;
}
```

### 객체끼리 대입 문제점 해결
```c
#include <iostream>
using namespace std;

class String
{
public:
	String(char ch, int nSize);
	~String();
	void operator = (const String& s); //전달되는 실제 메모리를 들고오겠다
	void SetData();
private:
	int nLength;
	char* pBuffer;
};

void String::operator=(const String& s)
{

	delete this->pBuffer; //this는 str1을 나타내줌
	this->nLength = s.nLength;
	this->pBuffer = new char[this->nLength + 1];
	strcpy_s(this->pBuffer, this->nLength + 1, s.pBuffer); //s는 str2 나타내줌

}

String::String(char ch, int nSize)
{
	nLength = nSize;
	pBuffer = new char[nLength + 1]; //문자열이라서 +1 해줌, 문자열 맨뒤 null문자
	memset(pBuffer, ch, nLength);
	pBuffer[nLength] = '\0';
	cout << "pBuffer :" << pBuffer << endl;
	cout << "nLength : " << nLength << endl;

}
String::~String()
{
	delete[] pBuffer;
}


void main()
{
	String str1('A',5);
	String str2('Z', 10);
	str1 = str2; //str1.operator(str2);
}
```

### shape클래스
```c
#include <iostream>
using namespace std;

class Shape
{
public:
	Shape() {}
	~Shape() {}
	Shape(int nx, int ny);
	
private:
	int x, y;
};
Shape::Shape(int nx, int ny)
{
	this->x = nx;
	this->y = ny;
}


void main()
{
	//객체를 생성하는 2가지 방법
	Shape sh(10, 20); //스택에 생성
	Shape* pSh = new Shape(10, 20); //힙에 생성
}
```

### shape클래스 상속받는 Rectangle,Circle클래스들 
```c
#include <iostream>
using namespace std;

class Shape
{
public:
	Shape() {}
	~Shape() {}
	Shape(double nx, double ny);
	virtual void Draw() = 0; //순수가상함수만듬 그림판보면 도형이 있는데, 어떤 도형을 그리고 해야하는지 너무 추상적이기 때문에 순수가상함수만듬
protected:
	double x, y;
};
Shape::Shape(double nx, double ny)
{
	this->x = nx;
	this->y = ny;
}
class Rectangle : public Shape
{
public:
	Rectangle() {}
	~Rectangle() {}
	Rectangle(double nx, double ny, double nWidth, int nHeight);
	void Draw()
	{
		cout << x << "," << y << "," << width << "" << height << endl;
	}
	
private:
	int width, height;

};

Rectangle::Rectangle(double nx, double ny, double nWidth, int nHeight)
{
	this->x = nx; //부모클래스한테 상속 받은거 
	this->y = ny;
	this->width = nWidth;
	this->height = nHeight;
}

class Circle : public Shape
{
public:
	Circle() {}
	~Circle() {}
	Circle(double nX, double nY, double nR);
	void Draw()
	{
		cout << x << "," << y << "," << r << endl;
	}
private:
	double r;

};
Circle::Circle(double nX, double nY, double nR)
{
	x = nX;
	y = nY;
	r = nR;
	
}

void main()
{
	
	Rectangle* pRect = new Rectangle(10, 20, 500, 600);
	pRect->Draw();

	Circle* pCir = new Circle(10, 20, 5 );
	pCir->Draw();

	Shape* pSp1 = (Shape*)pRect; //Rectangle 객체가 출력함
	pSp1->Draw();

	Shape* pSp2 = (Shape*)pCir; //오버라이딩 형태
	pSp2->Draw();
}
```

### shape클래스 상속받는 Rectangle,Circle클래스들 -> Rectangle상속받는 Square


```c
	#include <iostream>
	using namespace std;

	class Shape
	{
	public:
		Shape() {}
		~Shape() {}
		Shape(double nx, double ny);
		virtual void Draw() = 0; //순수가상함수만듬 그림판보면 도형이 있는데, 어떤 도형을 그리고 해야하는지 너무 추상적이기 때문에 순수가상함수만듬
	protected:
		double x, y;
	};
	Shape::Shape(double nx, double ny)
	{
		this->x = nx;
		this->y = ny;
	}
	class Rectangle : public Shape
	{
	public:
		Rectangle() {}
		~Rectangle() {}
		Rectangle(double nx, double ny, double nWidth, int nHeight);
		void Draw()
		{
			cout << x << "," << y << "," << width << "" << height << endl;
		}
	
	private:
		int width, height;

	};

	Rectangle::Rectangle(double nx, double ny, double nWidth, int nHeight)
	{
		this->x = nx; //부모클래스한테 상속 받은거 
		this->y = ny;
		this->width = nWidth;
		this->height = nHeight;
	}

	class Square : public Rectangle
	{
	public:
		Square() {} //디폴트생성자
		~Square() {} //디폴트소멸자
		void Drwa()
		{
			cout << x << "," << y << "," << length << endl;
		}
	private:
		int length;
		
	};
	
	class Circle : public Shape
	{
	public:
		Circle() {}
		~Circle() {}
		Circle(double nX, double nY, double nR);
		void Draw()
		{
			cout << x << "," << y << "," << r << endl;
		}
	private:
		double r;

	};
	Circle::Circle(double nX, double nY, double nR)
	{
		x = nX;
		y = nY;
		r = nR;
	
	}

	void main()
	{
	
		Rectangle* pRect = new Rectangle(10, 20, 500, 600);
		pRect->Draw();

		Circle* pCir = new Circle(10, 20, 5 );
		pCir->Draw();

		Shape* pSp1 = (Shape*)pRect; //Rectangle 객체가 출력함
		pSp1->Draw();

		Shape* pSp2 = (Shape*)pCir;
		pSp2->Draw();
	}
```

