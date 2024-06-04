## FlutterStudy2  

### <main.dart>  

```
import 'package:flutter/material.dart';
import 'package:flutter_application_1/other.dart';
void main() {
 runApp(const MyApp());
}
class MyApp extends StatelessWidget{
 const MyApp({super.key});
 @override
 Widget build(BuildContext context) {
 return const MaterialApp(
 debugShowCheckedModeBanner: false,
 title: 'Dice game',
 home: Login(),
);
}
}
class Login extends StatefulWidget{
 const Login({super.key});
 @override
 State<Login> createState() => _LoginState();
}
class _LoginState extends State<Login> {
 //TextField에 있는 값을 읽어야 할 때 사용한다.
 //controller를 생성하고 더이상 사용하지 않을 때 리소스의 낭비를 방지하기 위해
 //dispose method를 사용한다.
 TextEditingController controller = TextEditingController();
 TextEditingController controller2 = TextEditingController();
 @override
 Widget build(BuildContext context) {
 return Scaffold(
 appBar: AppBar(
 title: const Text('Log in'),
 backgroundColor: Colors.redAccent,
 centerTitle: true,
 leading: IconButton(icon: const Icon(Icons.menu), onPressed:() {}),
 actions:[
 IconButton(
 onPressed:() {},
 icon: const Icon(Icons.search),
),
],
),
 //Focus
 //FocusNode : 포커스를 받는 특정 위젯을 식별
 //FocusScope : 어떤 위젯들까지 포커스를 받는지 범위를 나타냄
 body: Builder(builder:(context) {
 return GestureDetector(
 onTap:() {
 FocusScope.of(context).unfocus();
},
 child: SingleChildScrollView(
 child: Column(
 children:[
 const Padding(padding: EdgeInsets.only(top: 50)),
 const Center(
 child: Text('로그인'),
),
 Form(
 child: Theme(
 data: ThemeData(
 primaryColor: Colors.teal,
 inputDecorationTheme: const InputDecorationTheme(
 labelStyle:
 TextStyle(color: Colors.teal, fontSize: 15.0),
),
),
 child: Container(
 padding: const EdgeInsets.all(40.0),
 child: Column(
 children:[
 TextField(
 controller: controller,
 decoration:
 const InputDecoration(labelText: 'Enter "dice"'),
 keyboardType: TextInputType.emailAddress,
),
 TextField(
 controller: controller2,
 decoration:
 const InputDecoration(labelText: 'Enter password'),
 keyboardType: TextInputType.text,
 obscureText: true,
),
 ButtonTheme(
 minWidth: 100.0,
 height: 50.0,
 child: ElevatedButton(
 child: Icon(Icons.arrow_forward_ios),
 style: ElevatedButton.styleFrom(
 primary: Colors.redAccent),
 onPressed:() {
 if(controller.text == 'dice' &&
 controller2.text == '1234') {
 Navigator.push(
 context,
 MaterialPageRoute(
 builder:(BuildContext context) =>
 const other()));
else if(controller.text == 'dice' &&
 controller2.text != '1234') {
 showSnackBar2(context);
else if(controller.text != 'dice' &&
 controller2.text == '1234') {
 showSnackBar(context);
else{
 showSnackBar3(context);
}
},
),
)
],
),
)),
)
],
),
),
);
}),
);
}
}
void showSnackBar(BuildContext context) {
 ScaffoldMessenger.of(context).showSnackBar(
 const SnackBar(
 content: Text(
 '로그인 정보를 다시 확인하세요.',
 textAlign: TextAlign.center,
),
 duration: Duration(seconds: 2),
 backgroundColor: Colors.blue,
),
);
}
void showSnackBar2(BuildContext context) {
 ScaffoldMessenger.of(context).showSnackBar(
 const SnackBar(
 content: Text(
 '비밀번호가 일치하지 않습니다.',
 textAlign: TextAlign.center,
),
 duration: Duration(seconds: 2),
 backgroundColor: Colors.blue,
),
);
}
void showSnackBar3(BuildContext context) {
 ScaffoldMessenger.of(context).showSnackBar(
 const SnackBar(
 content: Text(
 '절차를 다시 확인하세요.',
 textAlign: TextAlign.center,
),
 duration: Duration(seconds: 2),
 backgroundColor: Colors.blue,
),
);
}  
```  

### <other.dart>
```  
import 'package:flutter/material.dart';
class other extends StatefulWidget{
 const other({super.key});
 @override
 State<other> createState() => _otherState();
}
class _otherState extends State<other> {
 @override
 Widget build(BuildContext context) {
 return Scaffold(
 backgroundColor: Colors.redAccent,
 appBar: AppBar(
 backgroundColor: Colors.redAccent,
 title: const Text('others'),
),
 body: Center(
 child: Column(
 mainAxisAlignment: MainAxisAlignment.center,
 children:[
 const Padding(
 padding: EdgeInsets.all(32.0),
 child: Row(
 children:[Text('other')],
),
),
 const SizedBox(
 height: 60.0,
),
 ButtonTheme(
 minWidth: 100.0,
 height: 60.0,
 child: ElevatedButton(
 onPressed:() {},
 child: const Icon(
 Icons.play_arrow,
 size: 50.0,
),
),
),
],
),
),
);
}
}
```  

[ 결과 ]  

![image](https://github.com/jiwon0629/FlutterStudy/assets/149983498/74e49a5b-bd4c-4048-ba98-c4af0c4a9d46)




final & const는 더이상 바뀌지 않는 것
compile-time constant는 컴파일 시에 상수가 됨
const 변수는 선언과 동시에 초기화
컴파일시부터 상수화가 되어서 런타임시에도 반드시 그 값이 유지돼야 하는 변수는 
const변수를 사용한다.

1. const 변수는 컴파일 시에 상수화
2. final 변수는 런타임 시에 상수화
3. Compile-time constant = Run-time constant(커스텀 변수로써 컴파일 시에 상수화가 된다는 것은 런타임 시에도 value 값이 절대로 변하지 않는 상수로써의 특징을 유지한다는 의미이다.)
4. final 변수는 rebuild 될 수 있음(final 변수는 그 값이 변경되어야 한다면 rebuild 메소드 내에서 rebuild되어야 한다.)








Duration 엑세스 데이터 함수의 실행을 내가 원하는 시간만큼 딜레이 시킨다.
sleep은 Duration 함수의 Duration 변수를 인자값으로 받고있다.
ex) Duration time = Duration(seconds : 3);
    sleep(time);//실행이 되든 안되든 순서가 되면 3초간 지연된다.

Future.delayed(Duration 변수, 딜레이 후에 실행될 내용) //delayed를 만나면 지정한 시간만큼 실행이 중단되고 다음 코드로 넘어가게 된다. 다음 코드가 실행된 후에 지정한 시간이 지나면 다시 돌아온다.

Future 클래스는 비동기 작업을 할 때 사용
Future는 일정 소요시간 후에 실제 데이터나 에러를 반환
async 클래스는 await 메소드를 가지고 있음
 - await로 선언된 메소드는 응답이 처리될 때까지 대기


Set은 중복을 허용하지 않는다.
List대신 Set을 사용하면 최소한 난수 발생 과정에서 중복을 허용하지 않는다.
ex) Set<int> rainbow = {1,2,3,4,5,6};
1,2,3,4,5,5 => {1,2,3,4,5}

List<int>.generate(리스트의 사이즈, 숫자들을 생성하는 역할);
List<int>.generate(10,(i) => i+1); //리스트가 1부터 10까지의 10개의 숫자를 생성

[Shuffle]
void shuffle(
	List list,
	[int start = 0,
	int end]
)//인덱스 사이에 있는 요소들을 랜덤하게 섞어준다

cascade notation : 간단하게 한 객체의 멤버 함수를 호출하거나 속성에 간단하게 접근을 할 수 있다.
es) void main(){
	var test = List<int>.generate(10, (i) => i+1)..shuffle();//".."이 cascade notation
	print(test);
} =>결과는 1부터 10까지의 수를 랜덤하게 섞여서 출력한다


[sublist method]

List<E> sublist(
	int start,
	[int end]//end는 인덱스 번호 - 1이다.
)


ex) 
var colors = ["red", "green", "blue", "orange", "pink"];
print(colors.sublist(1, 3); // [green, blue]






[후위 연산자]

void main(){
	int i = 1;
	int j = i++;

	print(j);
} //증가되기 전의 값을 리턴한다. 결과는 1이다.



[전위 연산자]

void main(){
	int i = 1;
	int j = ++i;

	print(j);
} //증가시킨 후의 값을 리턴한다. 결과는 2이다.


//코딩셰프 - 조금 매운맛강좌 12
Thread
프로세스내에서 실행되는 흐름의 단위
Process vs. Program
Process 내에서 Thread는 실질적인 앱의 동작을 담당한다.

Dart는 싱글 스레드(한번에 오직 하나의 작업만 실행하며 실행되는 동안 코드 에상 존재하는 다른 작업들이 개입할 여지가 없다.)로 운영되는 언어

Event loop
플러터 앱을 실행시키는 순간 isolate라고 불리는 새로운 스레드 프로세스가 하나 생성되고 즉시 작업을 시작한다. 
스레드가 생성되는 순간 Dart는 자동적으로 3가지가 실행된다.
1. FIFO 방식으로 "Micro Task와 Event 준비" 
2. main 함수 실행
3. Event loop 실행
앱이 실행되고 Event loop가 이벤트 큐에 있는 이벤트들을 처리하기 직전에 먼저 Micro Task를 처리한다.

Future
코드상에서 새로운 Future를 객체화 시키면
1. 다트에 의해서 Future 객체가 내부적인 배열에 등록
2. Future 관련해서 실행되어야 하는 코드들이 이벤트 큐에 등록
3. 불완전한 Future 객체가 반환
4. Synchronous 방식으로 실행되어야 할 코드 먼저 실행
5. 최종적으로 실제적인 Data값이 Future 객체로 전달








[Async method]
1. 메서드를 통해서 나오는 결과들은 Future
2. Await 키워드를 만날때까지 synchronous 방식으로 코드처리
3. await 키워드를 만나면 future가 완료될 때까지 대기
4. future가 완료되자마자 그 다음 코드들을 실행






import 'package:flutter/material.dart';
void main() {
 runApp(const MyApp());
}
class MyApp extends StatelessWidget{
 const MyApp({super.key});
 @override
 Widget build(BuildContext context) {
 return MaterialApp(
 debugShowCheckedModeBanner: false,
 title: 'Future',
 theme: ThemeData(primarySwatch: Colors.blue),
 home: const Home(),
);
}
}
class Home extends StatefulWidget{
 const Home({super.key});
 @override
 State<Home> createState() => _HomeState();
}
class _HomeState extends State<Home> {
 String result = 'no data found';
 @override
 Widget build(BuildContext context) {
 return Scaffold(
 appBar: AppBar(
 title: const Text(
 'Future test',
 style: TextStyle(
 color: Colors.white,
),
),
 backgroundColor: Colors.blue,
 centerTitle: true,
 elevation: 0.0,
),
 body: Center(
 child: Padding(
 padding: const EdgeInsets.all(30.0),
 child: Column(
 mainAxisAlignment: MainAxisAlignment.center,
 children:[
 ElevatedButton(
 onPressed:() {
 futureTest();
},
 child: const Padding(
 padding: EdgeInsets.all(8.0),
 child: Text(
 'Future test',
 style: TextStyle(fontSize: 20.0),
),
),
),
 const SizedBox(
 height: 20.0,
),
 Text(
 result,
 style: const TextStyle(fontSize: 20.0, color: Colors.redAccent),
),
],
),
),
),
);
}
 void futureTest() {
 Future.delayed(const Duration(seconds: 3)).then((value) {
 setState(() {
 this.result = 'The data is fetched';
});
});
}
}
//=========================================================












결과화면








Null safety
1. 모든 변수는 null이 될 수 없으며, non-nullable 변수에는 null 값을 할당할 수 없음
(변수는 값이 할당되기 전에는 절대로 참조해서 사용할 수가 없다.)

2. non-nullable 변수를 위한 null check가 필요 없음
(non-nullable 변수는 null값을 가질 수 없다.)

3. "Class 내의 변수는" 반드시 선언과 동시에 초기화를 시켜야 함


API
Applicatioin Programming Interface
1. 일련의 표준화된 명령이나 기능 (appBar, backgroundColor, textStyle...)
2. 외부 시스템과 상호 작용을 할 수 있도록 중간에서 매개 역할자로써의 ARI

try ~ catch(예외처리)
try {
	실행에 실패할 수도 있는 코드
} catch(e){
	코드 실행에 실패할 경우 출력될 내용
	(예외처리 구문)
}

JSON VS XML
XML : eXtensible Markup Language
JSON : JavaScript Object Notation (키값과 value값을 1대1로 매핑시키는 구조)


[날씨앱]

main.dart

import 'package:flutter/material.dart';
import 'package:flutter_application_1/screens/loading.dart';
void main() {
 runApp(const MyApp());
}
class MyApp extends StatelessWidget{
 const MyApp({super.key});
 @override
 Widget build(BuildContext context) {
 return MaterialApp(
 debugShowCheckedModeBanner: false,
 title: 'Weather app',
 theme: ThemeData(primarySwatch: Colors.blue),
 home: const Loading(),
);
}
}


weather_screen.dart

import 'package:flutter/material.dart';
import 'package:google_fonts/google_fonts.dart';
//import 'package:flutter_svg/flutter_svg.dart';
import 'package:intl/intl.dart';
import 'package:timer_builder/timer_builder.dart';
import 'package:flutter_application_1/model/model.dart';
//import 'package:intl/intl_browser.dart';
class WeatherScreen extends StatefulWidget{
 WeatherScreen({this.parseWeatherData, this.parseAirPollution});
 final parseWeatherData;
 final parseAirPollution;
 @override
 State<WeatherScreen> createState() => _WeatherScreenState();
}
class _WeatherScreenState extends State<WeatherScreen> {
 late Model model = Model();
 late String cityName;
 late int temp;
 late Widget icon;
 late String des;
 late Widget airIcon;
 late Widget airState;
 late double dust1;
 late double dust2;
 var date = DateTime.now();
 @override
 void initState() {
 // TODO: implement initState
 super.initState();
 updateData(widget.parseWeatherData, widget.parseAirPollution);
}
 void updateData(dynamic weatherData, dynamic airData) {
 double temp2 = weatherData['main']['temp'];
 int condition = weatherData['weather'][0]['id'];
 des = weatherData['weather'][0]['description'];
 dust1 = airData['list'][0]['components']['pm10'];
 dust2 = airData['list'][0]['components']['pm2_5'];
 int index = airData['list'][0]['main']['aqi'];
 temp = temp2.round(); //round는 반올림
 cityName = weatherData['name'];
 icon = model.getWeatherIcon(condition)!;
 airIcon = model.getAirIcon(index)!;
 airState = model.getAirCondition(index)!;
 print(temp);
 print(cityName);
}
 String getSystemTime() {
 var now = DateTime.now();
 return DateFormat("h:mm a").format(now);
}
 @override
 Widget build(BuildContext context) {
 return Scaffold(
 backgroundColor: Colors.amber[800],
 appBar: AppBar(
 elevation: 0.0,
 backgroundColor: Colors.amber[800],
 leading: IconButton(
 icon: const Icon(Icons.near_me),
 onPressed:() {},
 iconSize: 30.0,
),
 actions:[
 IconButton(
 onPressed:() {},
 icon: const Icon(
 Icons.location_searching,
),
 iconSize: 30.0,
),
],
),
 body: Container(
 child: Stack(
 children:[
 Container(
 padding: const EdgeInsets.all(20.0),
 child: Column(
 mainAxisAlignment: MainAxisAlignment.spaceBetween,
 children:[
 Expanded(
 //공간 확보
 child: Column(
 mainAxisAlignment: MainAxisAlignment.spaceBetween,
 crossAxisAlignment: CrossAxisAlignment.start,
 children:[
 Column(
 crossAxisAlignment: CrossAxisAlignment.start,
 children:[
 const SizedBox(
 height: 150.0,
),
 Text(
 '$cityName',
 style: GoogleFonts.lato(
 fontSize: 35.0,
 fontWeight: FontWeight.bold,
 color: Colors.white),
),
 Row(
 children:[
 TimerBuilder.periodic(
(const Duration(minutes: 1)),
 builder:(context) {
 print('${getSystemTime()}');
 return Text(
 '${getSystemTime()}',
 style: GoogleFonts.lato(
 fontSize: 16.0, color: Colors.white),
);
},
),
 Text(
 DateFormat(' - EEEE, ').format(date),
 style: GoogleFonts.lato(
 fontSize: 16.0, color: Colors.white),
),
 Text(
 DateFormat('d MMM, yyy').format(date),
 style: GoogleFonts.lato(
 fontSize: 16.0, color: Colors.white),
),
],
)
],
),
 Column(
 crossAxisAlignment: CrossAxisAlignment.start,
 children:[
 Text(
 '$temp\u2103',
 style: GoogleFonts.lato(
 fontSize: 85.0,
 fontWeight: FontWeight.w300,
 color: Colors.white),
),
 Row(
 children:[
 icon,
 Text(
 '$des',
 style: GoogleFonts.lato(
 fontSize: 16.0, color: Colors.white),
),
],
)
],
)
],
),
),
 Column(
 children:[
 Divider(
 height: 15.0,
 thickness: 2.0,
 color: Colors.white30,
),
 Row(
 mainAxisAlignment: MainAxisAlignment.spaceBetween,
 children:[
 Column(
 children:[
 Text(
 'AQI(대기질지수)',
 style: GoogleFonts.lato(
 fontSize: 14.0, color: Colors.white),
),
 SizedBox(
 height: 10.0,
),
 airIcon,
 SizedBox(
 height: 10.0,
),
 airState,
],
),
 Column(
 children:[
 Text(
 '미세먼지',
 style: GoogleFonts.lato(
 fontSize: 14.0, color: Colors.white),
),
 SizedBox(
 height: 10.0,
),
 Text(
 '$dust1',
 style: GoogleFonts.lato(
 fontSize: 24.0,
 color: Colors.white,
),
),
 SizedBox(
 height: 10.0,
),
 Text(
 'μg/m3',
 style: GoogleFonts.lato(
 fontSize: 14.0,
 color: Colors.white,
 fontWeight: FontWeight.bold),
),
],
),
 Column(
 children:[
 Text(
 '초미세먼지',
 style: GoogleFonts.lato(
 fontSize: 14.0, color: Colors.white),
),
 SizedBox(
 height: 10.0,
),
 Text(
 '$dust2',
 style: GoogleFonts.lato(
 fontSize: 24.0,
 color: Colors.white,
),
),
 SizedBox(
 height: 10.0,
),
 Text(
 'μg/m3',
 style: GoogleFonts.lato(
 fontSize: 14.0,
 color: Colors.white,
 fontWeight: FontWeight.bold),
),
],
),
],
),
],
)
],
),
),
],
),
),
);
}
}









model.dart

import 'package:flutter/cupertino.dart';
import 'package:flutter_svg/flutter_svg.dart';
import 'package:flutter/material.dart';
class Model{
 //메소드의 타입이 Widget인 이유는 각 날씨의 상태를 수치화해서 그 수치에 맞는 이미지 파일을 불러와야 하기 때문이다.
 Widget? getWeatherIcon(int conditon) {
 if(conditon < 300) {
 return SvgPicture.asset(
 'svg/Cloud-Lightning.svg',
 color: Colors.black87,
);
else if(conditon < 600) {
 return SvgPicture.asset(
 'svg/Cloud-Snow-Alt.svg',
 color: Colors.black87,
);
else if(conditon == 800) {
 return SvgPicture.asset(
 'svg/Sun.svg',
 color: Colors.black87,
);
else if(conditon <= 804) {
 return SvgPicture.asset(
 'svg/Cloud-Sun.svg',
 color: Colors.black87,
);
}
 return null;
}
 Widget? getAirIcon(int index) {
 if(index == 1) {
 return Image.asset(
 'image/good.png',
 width: 37.0,
 height: 35.0,
);
else if(index == 2) {
 return Image.asset(
 'image/fair.png',
 width: 37.0,
 height: 35.0,
);
else if(index == 3) {
 return Image.asset(
 'image/moderate.png',
 width: 37.0,
 height: 35.0,
);
else if(index == 4) {
 return Image.asset(
 'image/poor.png',
 width: 37.0,
 height: 35.0,
);
else if(index == 5) {
 return Image.asset(
 'image/bad.png',
 width: 37.0,
 height: 35.0,
);
}
 return null;
}
 Widget? getAirCondition(int index) {
 if(index == 1) {
 return Text(
 '"매우좋음"',
 style: TextStyle(
 color: Colors.indigo,
 fontWeight: FontWeight.bold,
),
);
else if(index == 2) {
 return Text(
 '"좋음"',
 style: TextStyle(
 color: Colors.indigo,
 fontWeight: FontWeight.bold,
),
);
else if(index == 3) {
 return Text(
 '"보통"',
 style: TextStyle(
 color: Colors.black87,
 fontWeight: FontWeight.bold,
),
);
else if(index == 4) {
 return Text(
 '"나쁨"',
 style: TextStyle(
 color: Colors.black87,
 fontWeight: FontWeight.bold,
),
);
else if(index == 5) {
 return Text(
 '"매우나쁨"',
 style: TextStyle(
 color: Colors.black87,
 fontWeight: FontWeight.bold,
),
);
}
 return null;
}
}

network.dart

import 'package:http/http.dart' as http;
import 'dart:convert'; //jsonDecode를 사용할 수 있음
class Network{
 final String url;
 final String url2;
 Network(this.url, this.url2);
 Future<dynamic> getJsonData() async{
 //날씨 데이터 타입은 다양하기 때문에 dynamic
 //json parshing
 final response = await http.get(Uri.parse(url));
 if(response.statusCode == 200) {
 String jsonData = response.body;
 //jsonDecode의 타입은 dynamic type이므로 값을 변수에 담으려면 var을 사용해야한다.
 var parshingData = jsonDecode(jsonData);
 return parshingData;
}
}
 Future<dynamic> getAirData() async{
 //날씨 데이터 타입은 다양하기 때문에 dynamic
 //json parshing
 final response = await http.get(Uri.parse(url2));
 if(response.statusCode == 200) {
 String jsonData = response.body;
 //jsonDecode의 타입은 dynamic type이므로 값을 변수에 담으려면 var을 사용해야한다.
 var parshingData = jsonDecode(jsonData);
 return parshingData;
}
}
}









loading.dart

import 'package:flutter/material.dart';
import 'package:flutter_application_1/data/my_location.dart';
import 'package:flutter_application_1/data/network.dart';
import 'package:flutter_application_1/screens/weather_screen.dart';
const apikey = '9a882db6a1591f35fd544a33542ce127';
//info.plist, pubspec.yaml, menifest
class Loading extends StatefulWidget{
 const Loading({super.key});
 @override
 State<Loading> createState() => _LoadingState();
}
class _LoadingState extends State<Loading> {
 late double latitude3;
 late double longitude3;
 @override
 void initState() {
 //TODO: implement initState
 super.initState();
 getLocation();
}
 void getLocation() async{
 //LocationPermission permission = await Geolocator.requestPermission();
 MyLocation myLocation = MyLocation();
 //await는 Future의 값이 return될 때까지 기다려야 한다는 의미이다.
 //위도와 경도 값이 포지션 변수에 할당 될 때까지 기다리기 위해서 await를 사용한다.
 await myLocation.getMyCurrentLocation(); //getMyCurrentLocation메소드를 기다림
 latitude3 = myLocation.latitude2;
 longitude3 = myLocation.longitude2;
 print(latitude3);
 print(longitude3);
 Network network = Network(
 //'https://samples.openweathermap.org/data/2.5/weather?q=London&appid=b1b15e88fa797225412429c1c50c122a1');
 'https://api.openweathermap.org/data/2.5/weather?lat=$latitude3&lon=$longitude3&appid=$apikey&units=metric',
 'http://api.openweathermap.org/data/2.5/air_pollution?lat=$latitude3&lon=$longitude3&appid=$apikey');
 var weatherData =
 await network.getJsonData(); //parshing 데이터를 return해주고 있기 때문에 await
 print(weatherData);
 var airData = await network.getAirData();
 print(airData);
 //weather_screen 페이지로 이동 시 weatherData, airData에 담긴 데이터들이 동시에 전달된다.
 Navigator.push(context, MaterialPageRoute(builder:(context) {
 return WeatherScreen(
 parseWeatherData: weatherData,
 parseAirPollution: airData,
);
}));
}
 // Future<void> fetchData() async {
 // var myJson = parshingData['weather'][0]['description'];
 // print(myJson);
 // var wind = parshingData['wind']['speed'];
 // print(wind);
 // var id = parshingData['id'];
 // print(id);
 // } else {
 // print(response.statusCode);
 // }
 // }
 @override
 Widget build(BuildContext context) {
 return const Scaffold(
 body: Center(
 child: ElevatedButton(
 onPressed: null,
 child: Text(
 'Get my location',
 style: TextStyle(color: Colors.white),
),
),
));
}
}

my_location.dart

import 'package:geolocator/geolocator.dart'; //날씨 앱
class MyLocation{
 late double latitude2;
 late double longitude2;
 Future<void> getMyCurrentLocation() async{
 //await가 있으면 async가 있어야 함
 try{
 //Geolocator 패키지를 사용해서 위도와 경도 값을 position 변수에 전달하게 된다.
 //이를 위해서 await를 사용해서 async 방식으로 메소드가 동작하게 된다.
 Position position = await Geolocator.getCurrentPosition(
 desiredAccuracy: LocationAccuracy.high);
 latitude2 = position.latitude;
 longitude2 = position.longitude;
 print(latitude2);
 print(longitude2);
catch(e) {
 print('There was a problem with the internet connection.');
}
}
}

결과화면[수정된 부분도 있지만 그건 flutter_application_1에서 확인해보기]


[Keys]
1. 위젯의 State를 보존
2. 위젯이나 요소들을 유니크하게 식별

- State란 UI가 변경되도록 영향을 미치는 데이터이다.

Value Key
Value 값을 State로 갖는 Stateful Widget의 State를 보존하길 원할 때
ex) id, pwd에서 입력한 값

1. Flutter는 기본적으로 위젯의 타입으로 식별
2. Stateful위젯의 식별을 위해서는 Key가 필요
3. Value key는 value값을 가지는 Stateful Widget에 사용

Global Key
전역변수(Global Variable)란 메소드의 외부에서 선언된 변수이고 여러 개의 메소드에서 동시에 사용될 수 있어야 하기 때문에 프로그램 어디에서나 접근을 할 수 있는 변수이다.

import 'package:flutter/material.dart';
void main() {
 runApp(const MyApp());
}
class MyApp extends StatelessWidget{
 const MyApp({super.key});
 @override
 Widget build(BuildContext context) {
 return MaterialApp(
 theme: ThemeData(primarySwatch: Colors.blue),
 home: MyKey(),
);
}
}
class MyKey extends StatelessWidget{
 final counterKey = GlobalKey<_CounterState>();
 @override
 Widget build(BuildContext context) {
 return Scaffold(
 appBar: AppBar(
 title: Text('Global key'),
),
 body: Center(
 child: Counter(
 key: counterKey,
),
),
 floatingActionButton: FloatingActionButton(
 onPressed:() {
 counterKey.currentState!.increment();
 print(counterKey.currentState!.count);
},
 child: const Icon(
 Icons.add,
 color: Colors.white,
),
),
);
}
}
class Counter extends StatefulWidget{
 const Counter({super.key});
 @override
 State<Counter> createState() => _CounterState();
}
class _CounterState extends State<Counter> {
 int count = 0;
 void increment() {
 setState(() {
 count++;
});
}
 @override
 Widget build(BuildContext context) {
 return Center(
 child: Text(
 'Count number :$count',
 style: TextStyle(fontSize: 20.0),
),
);
}
}

[결과화면]

[Stream]


즉시 사용가능 
기다려야 사용가능
단일 데이터
ex) String, int, double
ex) int
ex) Future<int>(async방식)
전달이 되면 그 즉시 사용할 수 있는 데이터
복수 데이터
ex) List
ex) List<int>
ex) Stream<int>
int 데이터가 언제라도 스트림에 전달될 수 있으며 구독하고 있는 한 스트림에 데이터가 전달될 때마다 즉시 알 수 있게 된다.



rules_version = '2';
service cloud.firestore {
//전체 데이터베이스에 포괄적으로 적용되는 리퀘스트
  match /databases/{database}/documents {
    
    //match : 어떤 리퀘스트를 전달하고 어떤 리퀘스트에 적용될지 지정할 수 있다.
    //match/chats{
    //만약 auth request에 어떤 정보가 존재하면 즉, 사용자가 인증이 되면 데이터를 쓰고 읽을 수 있다.
    	//allow read, write : if request.auth != null;
      //create : 단순히 데이터를 생성하는 기능
      
   // }
   
    //{doucument=**} : 모든 다큐먼트의 접근을 가능하게 하겠다는 의미
    match /{document=**} {
    allow read, write : if request.auth != null;
      //allow read, write: if request.time < timestamp.date(2023, 11, 12);
    }
  }
}















[채팅앱]

main.dart

import 'package:flutter/material.dart';
import 'package:flutter_application_2/screens/chat_screen.dart';
import 'package:flutter_application_2/screens/main_screen.dart';
import 'package:firebase_core/firebase_core.dart';
import 'package:firebase_auth/firebase_auth.dart';
void main() async{
 WidgetsFlutterBinding.ensureInitialized();
 await Firebase.initializeApp();
 runApp(const MyApp());
}
class MyApp extends StatelessWidget{
 const MyApp({super.key});
 @override
 Widget build(BuildContext context) {
 return MaterialApp(
 title: 'Chatting app',
 theme: ThemeData(primarySwatch: Colors.blue),
 home: StreamBuilder(
 stream: FirebaseAuth.instance.authStateChanges(),
 builder:(context, snapshot) {
 if(snapshot.hasData) {
 return ChatScreen();
}
 return LoginSignupScreen();
},
),
 debugShowCheckedModeBanner: false,
);
}
}
palette.dart

import 'package:flutter/painting.dart';
class Palette{
 static const Color iconColor = Color(0xFFB6C7D1);
 static const Color activeColor = Color(0xFF09126C);
 static const Color textColor1 = Color(0XFFA7BCC7);
 static const Color textColor2 = Color(0XFF9BB3C0);
 static const Color facebookColor = Color(0xFF3B5999);
 static const Color googleColor = Color(0xFFDE4B39);
 static const Color backgroundColor = Color(0xFFECF3F9);
}


main_screen.dart


import 'package:flutter/material.dart';
//import 'package:flutter_application_2/add_image/add_image.dart';
import 'package:flutter_application_2/config/palette.dart';
import 'package:firebase_auth/firebase_auth.dart';
import 'package:flutter_application_2/screens/chat_screen.dart';
import 'package:modal_progress_hud_nsn/modal_progress_hud_nsn.dart';
import 'package:cloud_firestore/cloud_firestore.dart';
class LoginSignupScreen extends StatefulWidget{
 const LoginSignupScreen({super.key});
 @override
 State<LoginSignupScreen> createState() => _LoginSignupScreenState();
}
class _LoginSignupScreenState extends State<LoginSignupScreen> {
 //외부에서 함부로 접근할 수 없도록 _붙여서 사용한다.
 //사용자의 등록과 인증에 사용한다.
 final _authentication = FirebaseAuth.instance;
 bool isSignupScreen = true;
 bool showSpinner = false;
 final _formKey = GlobalKey<FormState>();
 String userName = '';
 String userEmail = '';
 String userPassword = '';
 void _tryValidation() {
 //모든 텍스트 필드의 폼필드 validator를 작동시킬 수 있게 된다.
 final isValid = _formKey.currentState!.validate();
 if(isValid) {
 _formKey.currentState!.save();
}
}
 void showAlert(BuildContext context) {
 showDialog(
 context: context,
 builder:(context) {
 return const Dialog(
 backgroundColor: Colors.white,
);
});
}
 @override
 Widget build(BuildContext context) {
 return Scaffold(
 backgroundColor: Palette.backgroundColor,
 //위젯을 원하는 곳에 위치시킬 수 있다.
 body: ModalProgressHUD(
 inAsyncCall: showSpinner,
 child: GestureDetector(
 onTap:() {
 //키보드 해제
 FocusScope.of(context).unfocus();
},
 child: Stack(
 children:[
 //배경
 Positioned(
 right: 0,
 left: 0,
 top: 0,
 child: Container(
 height: 300,
 decoration: const BoxDecoration(
 image: DecorationImage(
 image: AssetImage('image/red.jpg'), fit: BoxFit.fill),
),
 child: Container(
 padding: const EdgeInsets.only(top: 90, left: 20),
 child: Column(
 crossAxisAlignment: CrossAxisAlignment.start,
 //RichText는 글자의 폰트 크기나 특징이 다를때
 //TextSpan은 글자나 문단을 모아서 구성할 수 있음
 children:[
 RichText(
 text: TextSpan(
 text: 'Welcome',
 style: const TextStyle(
 letterSpacing: 1.0,
 fontSize: 25,
 color: Colors.white,
),
 children:[
 TextSpan(
 text: isSignupScreen
 ? ' to Yummy chat!'
 : ' back',
 style: const TextStyle(
 letterSpacing: 1.0,
 fontSize: 25,
 color: Colors.white,
 fontWeight: FontWeight.bold,
),
)
],
),
),
 const SizedBox(
 height: 5.0,
),
 Text(
 isSignupScreen
 ? 'Signup to continue'
 : 'Signin to continue',
 style: const TextStyle(
 letterSpacing: 1.0,
 color: Colors.white,
),
),
],
),
),
),
),
 //텍스트 폼 필드
 AnimatedPositioned(
 duration: const Duration(milliseconds: 500),
 curve: Curves.easeIn,
 top: 180,
 child: AnimatedContainer(
 duration: const Duration(milliseconds: 500),
 curve: Curves.easeIn,
 padding: const EdgeInsets.all(20.0),
 height: isSignupScreen ? 280.0 : 250.0,
 width: MediaQuery.of(context).size.width - 40,
 margin: const EdgeInsets.symmetric(horizontal: 20.0),
 decoration: BoxDecoration(
 color: Colors.white,
 borderRadius: BorderRadius.circular(15.0),
 boxShadow:[
 BoxShadow(
 color: Colors.black.withOpacity(0.3),
 blurRadius: 15,
 spreadRadius: 5,
),
],
),
 child: SingleChildScrollView(
 padding: const EdgeInsets.only(bottom: 20),
 child: Column(
 children:[
 Row(
 mainAxisAlignment: MainAxisAlignment.spaceAround,
 children:[
 GestureDetector(
 onTap:() {
 setState(() {
 isSignupScreen = false;
});
},
 child: Column(
 children:[
 Text(
 'LOGIN',
 style: TextStyle(
 fontSize: 16.0,
 fontWeight: FontWeight.bold,
 //사명 연산자 구조
 //로그인 화면이 선택되었을 때 팔레트에 있는 activeColor를 보여주고 그렇지 않을 경우
 //팔레트에 있는 textColocr1을 보여준다.
 color: !isSignupScreen
 ? Palette.activeColor
 : Palette.textColor1,
),
),
 if(!isSignupScreen)
 Container(
 margin: const EdgeInsets.only(top: 3),
 height: 2,
 width: 55,
 color: Colors.orange,
),
],
),
),
 GestureDetector(
 onTap:() {
 setState(() {
 //사용자가 signup 메뉴를 선택했다는 의미
 isSignupScreen = true;
});
},
 child: Column(
 children:[
 Row(
 children:[
 Text(
 'SIGNUP',
 style: TextStyle(
 fontSize: 16.0,
 fontWeight: FontWeight.bold,
 color: isSignupScreen
 ? Palette.activeColor
 : Palette.textColor1,
),
),
 const SizedBox(
 width: 15,
),
 GestureDetector(
 onTap:() {
 showAlert(context);
},
 child: Icon(
 Icons.image,
 color: isSignupScreen
 ? Colors.cyan
 : Colors.grey[300],
),
),
],
),
 if(isSignupScreen)
 Container(
 margin: const EdgeInsets.fromLTRB(
 0, 3, 35, 0),
 height: 2,
 width: 55,
 color: Colors.orange,
),
],
),
),
],
),
 if(isSignupScreen)
 Container(
 margin: const EdgeInsets.only(top: 20),
 child: Form(
 key: _formKey,
 child: Column(
 children:[
 TextFormField(
 key: const ValueKey(1),
 validator:(value) {
 if(value!.isEmpty || value.length < 4) {
 return 'Please enter at least 4 characters.';
}
 return null;
},
 onSaved:(value) {
 userName = value!;
},
 onChanged:(value) {
 userName = value;
},
 decoration: const InputDecoration(
 prefixIcon: Icon(
 Icons.account_circle,
 color: Palette.iconColor,
),
 enabledBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 focusedBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 hintText: 'User name',
 hintStyle: TextStyle(
 fontSize: 14,
 color: Palette.textColor1,
),
 //contentPadding은 폭을 줄인다.
 contentPadding: EdgeInsets.all(10),
),
),
 const SizedBox(
 height: 8,
),
 TextFormField(
 keyboardType: TextInputType.emailAddress,
 key: const ValueKey(2),
 validator:(value) {
 if(value!.isEmpty ||
 value.contains("@")) {
 return 'Please enter a valid email address.';
}
 return null;
},
 onSaved:(value) {
 userEmail = value!;
},
 onChanged:(value) {
 userEmail = value;
},
 decoration: const InputDecoration(
 prefixIcon: Icon(
 Icons.email,
 color: Palette.iconColor,
),
 enabledBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 focusedBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 hintText: 'email',
 hintStyle: TextStyle(
 fontSize: 14,
 color: Palette.textColor1,
),
 //contentPadding은 폭을 줄인다.
 contentPadding: EdgeInsets.all(10),
),
),
 const SizedBox(
 height: 8,
),
 TextFormField(
 //obscureText : 패스워드 가리는 용도
 obscureText: true,
 key: const ValueKey(3),
 validator:(value) {
 if(value!.isEmpty || value.length < 6) {
 return 'Password must be at least 7 characters long.';
}
 return null;
},
 onSaved:(value) {
 userPassword = value!;
},
 onChanged:(value) {
 userPassword = value;
},
 decoration: const InputDecoration(
 prefixIcon: Icon(
 Icons.lock,
 color: Palette.iconColor,
),
 enabledBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 focusedBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 hintText: 'password',
 hintStyle: TextStyle(
 fontSize: 14,
 color: Palette.textColor1,
),
 //contentPadding은 폭을 줄인다.
 contentPadding: EdgeInsets.all(10),
),
),
],
),
),
),
 if(!isSignupScreen)
 Container(
 margin: const EdgeInsets.only(top: 20),
 child: Form(
 key: _formKey,
 child: Column(
 children:[
 TextFormField(
 key: const ValueKey(4),
 validator:(value) {
 if(value!.isEmpty ||
 value.contains("@")) {
 return 'Please enter a valid email address.';
}
 return null;
},
 onSaved:(value) {
 userEmail = value!;
},
 onChanged:(value) {
 userEmail = value;
},
 decoration: const InputDecoration(
 prefixIcon: Icon(
 Icons.email,
 color: Palette.iconColor,
),
 enabledBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 focusedBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 hintText: 'email',
 hintStyle: TextStyle(
 fontSize: 14,
 color: Palette.textColor1,
),
 //contentPadding은 폭을 줄인다.
 contentPadding: EdgeInsets.all(10),
),
),
 const SizedBox(
 height: 8.0,
),
 TextFormField(
 key: const ValueKey(5),
 validator:(value) {
 if(value!.isEmpty || value.length < 6) {
 return 'Password must be at least 7 characters long.';
}
 return null;
},
 onSaved:(value) {
 userPassword = value!;
},
 onChanged:(value) {
 userPassword = value;
},
 decoration: const InputDecoration(
 prefixIcon: Icon(
 Icons.lock,
 color: Palette.iconColor,
),
 enabledBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 focusedBorder: OutlineInputBorder(
 borderSide: BorderSide(
 color: Palette.textColor1),
 borderRadius: BorderRadius.all(
 Radius.circular(35.0),
),
),
 hintText: 'password',
 hintStyle: TextStyle(
 fontSize: 14,
 color: Palette.textColor1,
),
 //contentPadding은 폭을 줄인다.
 contentPadding: EdgeInsets.all(10),
),
),
],
),
),
)
],
),
),
),
),
 //전송버튼
 AnimatedPositioned(
 duration: const Duration(milliseconds: 500),
 curve: Curves.easeIn,
 top: isSignupScreen ? 430 : 390,
 right: 0,
 left: 0,
 child: Center(
 child: Container(
 padding: const EdgeInsets.all(15),
 height: 90,
 width: 90,
 decoration: BoxDecoration(
 color: Colors.white,
 borderRadius: BorderRadius.circular(50),
),
 child: GestureDetector(
 onTap:() async{
 setState(() {
 showSpinner = true;
});
 if(isSignupScreen) {
 _tryValidation();
 try{
 final newUser = await _authentication
.createUserWithEmailAndPassword(
 email: userEmail,
 password: userPassword,
);
 //새로운 데이터베이스에 추가하는 코드
 await FirebaseFirestore.instance
.collection('user')
.doc(newUser.user!.uid)
.set(
{
 'userName': userName,
 'email': userEmail,
},
);
 if(newUser.user != null) {
 Navigator.push(
 context,
 MaterialPageRoute(builder:(context) {
 return ChatScreen();
}),
);
 setState(() {
 showSpinner = false;
});
}
catch(e) {
 print(e);
 if(mounted) {
 ScaffoldMessenger.of(context).showSnackBar(
 const SnackBar(
 content: Text(
 'Please check your email and password'),
 backgroundColor: Colors.blue,
),
);
 setState(() {
 showSpinner = false;
});
}
}
}
 if(!isSignupScreen) {
 _tryValidation();
 try{
 final newUser = await _authentication
.signInWithEmailAndPassword(
 email: userEmail,
 password: userPassword,
);
 if(newUser.user != null) {
 // Navigator.push(
 // context,
 // MaterialPageRoute(builder: (context) {
 // return ChatScreen();
 // }),
 // );
}
catch(e) {
 print(e);
}
}
},
 child: Container(
 decoration: BoxDecoration(
 gradient: const LinearGradient(
 colors:[Colors.orange, Colors.red],
 begin: Alignment.topLeft,
 end: Alignment.bottomRight),
 borderRadius: BorderRadius.circular(30),
 boxShadow:[
 BoxShadow(
 color: Colors.black.withOpacity(0.3),
 spreadRadius: 1,
 blurRadius: 1,
 //offset은 한 지점에서 다른 지점으로까지의 거리
 //즉 버튼 그림자 효과가 가지는 버튼으로부터의 수직, 수평 거리
 offset: const Offset(0, 1),
),
],
),
 child: const Icon(
 Icons.arrow_forward,
 color: Colors.white,
),
),
),
),
),
),
 //구글 로그인 버튼
 AnimatedPositioned(
 duration: const Duration(milliseconds: 500),
 curve: Curves.easeIn,
 top: isSignupScreen
 ? MediaQuery.of(context).size.height - 125
 : MediaQuery.of(context).size.height - 165,
 right: 0,
 left: 0,
 child: Column(
 children:[
 Text(isSignupScreen ? 'or Signup with' : 'or Signin with'),
 const SizedBox(
 height: 10,
),
 TextButton.icon(
 onPressed:() {},
 style: TextButton.styleFrom(
 primary: Colors.white,
 minimumSize: const Size(155, 40),
 shape: RoundedRectangleBorder(
 borderRadius: BorderRadius.circular(20),
),
 backgroundColor: Palette.googleColor,
),
 icon: const Icon(Icons.add),
 label: const Text('Google'),
),
],
),
),
],
),
),
),
);
}
}







add_image.dart

import 'package:flutter/material.dart';
class AddImage extends StatefulWidget{
 const AddImage({super.key});
 @override
 State<AddImage> createState() => _AddImageState();
}
class _AddImageState extends State<AddImage> {
 @override
 Widget build(BuildContext context) {
 return Container(
 padding: const EdgeInsets.only(top: 10),
 width: 150,
 height: 300,
 child: Column(
 children:[
 const CircleAvatar(
 radius: 40,
 backgroundColor: Colors.blue,
),
 const SizedBox(
 height: 10,
),
 OutlinedButton.icon(
 onPressed:() {},
 icon: const Icon(Icons.image),
 label: const Text('Add image'),
),
 const SizedBox(
 height: 80,
),
 TextButton.icon(
 onPressed:() {
 Navigator.pop(context);
},
 icon: const Icon(Icons.close),
 label: const Text('Close'),
),
],
),
);
}
}






chat_screen.dart

import 'package:flutter/material.dart';
import 'package:firebase_auth/firebase_auth.dart';
//import 'package:cloud_firestore/cloud_firestore.dart';
import 'package:flutter_application_2/chatting/chat/message.dart';
import 'package:flutter_application_2/chatting/chat/new_message.dart';
class ChatScreen extends StatefulWidget{
 const ChatScreen({super.key});
 @override
 State<ChatScreen> createState() => _ChatScreenState();
}
class _ChatScreenState extends State<ChatScreen> {
 final _authentication = FirebaseAuth.instance;
 //값을 초기화 시키지 않을 것이기 때문에 nullable타입을 알려주기 위해 ? 사용한다.
 User? loggedUser;
 @override
 void initState() {
 // TODO: implement initState
 super.initState();
 getCurrentUser();
}
 void getCurrentUser() {
 try{
 final user = _authentication.currentUser;
 if(user != null) {
 loggedUser = user;
 print(loggedUser!.email);
}
catch(e) {
 print(e);
}
}
 @override
 Widget build(BuildContext context) {
 return Scaffold(
 appBar: AppBar(
 title: const Text('Chat screen'),
 actions:[
 IconButton(
 onPressed:() {
 _authentication.signOut();
},
 icon: const Icon(
 Icons.exit_to_app_sharp,
 color: Colors.white,
),
),
],
),
 body: Container(
 child: const Column(
 children:[
 Expanded(
 child: Messages(),
),
 NewMessage(),
],
),
));
}
}

new_message.dart

import 'package:flutter/material.dart';
import 'package:cloud_firestore/cloud_firestore.dart';
import 'package:firebase_auth/firebase_auth.dart';
class NewMessage extends StatefulWidget{
 const NewMessage({super.key});
 @override
 State<NewMessage> createState() => _NewMessageState();
}
class _NewMessageState extends State<NewMessage> {
 var _userEnterMessage = '';
 final _controller = TextEditingController();
 void _sendMessage() async{
 FocusScope.of(context).unfocus();
 final user = FirebaseAuth.instance.currentUser;
 final userData = await FirebaseFirestore.instance
.collection('user')
.doc(user!.uid)
.get();
 FirebaseFirestore.instance.collection('chat').add({
 'text': _userEnterMessage,
 'time': Timestamp.now(),
 'userID': user!.uid,
 'userName': userData.data()!['userName'],
});
 _controller.clear();
}
 @override
 Widget build(BuildContext context) {
 return Container(
 margin: const EdgeInsets.only(top: 8),
 padding: const EdgeInsets.all(8),
 child: Row(
 children:[
 Expanded(
 child: TextField(
 maxLines: null,
 controller: _controller,
 decoration: const InputDecoration(labelText: 'Send a message...'),
 onChanged:(value) {
 setState(() {
 _userEnterMessage = value;
});
},
),
),
 IconButton(
 //버튼을 누를 수 있게 활성화 하는 기능
 onPressed: _userEnterMessage.trim().isEmpty ? null : _sendMessage,
 icon: Icon(Icons.send),
 color: Colors.blue,
),
],
),
);
}
}

message.dart

import 'package:flutter/material.dart';
import 'package:cloud_firestore/cloud_firestore.dart';
import 'package:flutter_application_2/chatting/chat/chat_bubble.dart';
import 'package:firebase_auth/firebase_auth.dart';
class Messages extends StatelessWidget{
 const Messages({super.key});
 @override
 Widget build(BuildContext context) {
 final user = FirebaseAuth.instance.currentUser;
 return StreamBuilder(
 stream: FirebaseFirestore.instance
.collection('chat')
.orderBy('time', descending: true)
.snapshots(),
 builder:(context,
 AsyncSnapshot<QuerySnapshot<Map<String, dynamic>>> snapshot) {
 if(snapshot.connectionState == ConnectionState.waiting) {
 return const Center(
 child: CircularProgressIndicator(),
);
}
 final chatDocs = snapshot.data!.docs;
 return ListView.builder(
 reverse: true,
 itemCount: chatDocs.length,
 itemBuilder:(context, index) {
 return ChatBubbles(
 chatDocs[index]['text'],
 chatDocs[index]['userID'].toString() == user!.uid,
 chatDocs[index]['userName']);
},
);
},
);
}
}

chat_bubble.dart

import 'package:flutter/material.dart';
import 'package:flutter_chat_bubble/bubble_type.dart';
import 'package:flutter_chat_bubble/chat_bubble.dart';
import 'package:flutter_chat_bubble/clippers/chat_bubble_clipper_8.dart';
class ChatBubbles extends StatelessWidget{
 const ChatBubbles(this.message, this.isMe, this.userName, {super.key});
 final String message;
 final bool isMe;
 final String userName;
 @override
 Widget build(BuildContext context) {
 return Row(
 mainAxisAlignment: isMe ? MainAxisAlignment.end : MainAxisAlignment.start,
 children:[
 if(isMe)
 Padding(
 padding: const EdgeInsets.fromLTRB(0, 0, 5, 0),
 child: ChatBubble(
 clipper: ChatBubbleClipper8(type: BubbleType.sendBubble),
 alignment: Alignment.topRight,
 margin: const EdgeInsets.only(top: 20),
 backGroundColor: Colors.blue,
 child: Container(
 constraints: BoxConstraints(
 maxWidth: MediaQuery.of(context).size.width * 0.7,
),
 child: Column(
 crossAxisAlignment:
 isMe ? CrossAxisAlignment.end : CrossAxisAlignment.start,
 children:[
 Text(
 userName,
 style: const TextStyle(
 fontWeight: FontWeight.bold,
 color: Colors.white,
),
),
 Text(
 message,
 style: const TextStyle(
 color: Colors.white,
),
),
],
),
),
),
),
 if(!isMe)
 Padding(
 padding: const EdgeInsets.fromLTRB(5, 0, 0, 0),
 child: ChatBubble(
 clipper: ChatBubbleClipper8(type: BubbleType.receiverBubble),
 backGroundColor: const Color(0xffE7E7ED),
 margin: const EdgeInsets.only(top: 20),
 child: Container(
 constraints: BoxConstraints(
 maxWidth: MediaQuery.of(context).size.width * 0.7,
),
 child: Column(
 crossAxisAlignment:
 isMe ? CrossAxisAlignment.end : CrossAxisAlignment.start,
 children:[
 Text(
 userName,
 style: const TextStyle(
 fontWeight: FontWeight.bold,
 color: Colors.black,
),
),
 Text(
 message,
 style: const TextStyle(
 color: Colors.black,
),
),
],
),
),
),
)
],
);
}
}

[결과화면]



[Provider]

State Management
1. State란 어떤 형태이든 앱 화면 즉, UI에 변화가 생기도록 영향을 미치는 데이터
2. 앱 수준의 데이터는 서버와 연동해서 사용자 인증을 한다든지 또는 서버에 저장된 정보를 끌어와서 화면에 보여주는 등 앱의 화면에 변화를 일으키는 모든 데이터를 말한다.
3. 위젯 수준의 데이터란 가령, 빈 체크박스에 사용자가 터치를 하면 체크 표시가 생기게 되고 이 상태를 위젯 차원에서 해결해서 화면에 변화가 생기게 하는 데이터를 말한다.

setState method
state가 변해서 UI를 다시 그려야 할 때 setState를 사용한다.
1. 위젯 라이프 사이클에 Build method를 호출해서 UI를 랜더링하게 만드는 것
2. Flutter가 기본 제공하는 state management

setState method 사용시 문제점
1. 비효율성
2. 동시에 다른 위젯의 state를 업데이트 시켜주지 못함

State management 정의 
1. 위젯이 쉽게 데이터에 접근할 수 있는 방법
2. 변화된 데이터에 맞추

============================================================
새 프로젝트 생성 방법
보기 -> 명령 팔레트

const를 없애려면
analysis_options.yaml -> # include: package:flutter_lints/flutter.yaml


main.dart

import 'package:flutter/material.dart';
import 'package:flutter_application_3/fish_model.dart';
import 'package:provider/provider.dart';
void main() {
 runApp(const MyApp());
}
class MyApp extends StatelessWidget{
 const MyApp({super.key});
 @override
 Widget build(BuildContext context) {
 return Provider(
 create:(context) => FishModel(name: 'Salmon', number: 10, size: 'big'),
 child: MaterialApp(
 home: FishOrder(),
),
);
}
}
class FishOrder extends StatelessWidget{
 const FishOrder({super.key});
 @override
 Widget build(BuildContext context) {
 return Scaffold(
 appBar: AppBar(
 title: Text('Fish Order'),
),
 body: Center(
 child: Column(
 children:[
 Text(
 'Fish name : ${Provider.of<FishModel>(context).name}',
 style: TextStyle(fontSize: 20),
),
 SizedBox(
 height: 20,
),
 High()
],
),
),
);
}
}
class High extends StatelessWidget{
 const High({super.key});
 @override
 Widget build(BuildContext context) {
 return Column(
 children:[
 Text(
 'SpicyA is located at high place',
 style: TextStyle(fontSize: 16),
),
 SizedBox(
 height: 20,
),
 SpicyA()
],
);
}
}
class SpicyA extends StatelessWidget{
 const SpicyA({super.key});
 @override
 Widget build(BuildContext context) {
 return Column(
 children:[
 Text(
 'Fish number : ${Provider.of<FishModel>(context).number}',
 style: TextStyle(
 fontSize: 16,
 color: Colors.red,
 fontWeight: FontWeight.bold,
),
),
 Text(
 'Fish size : ${Provider.of<FishModel>(context).size}',
 style: TextStyle(
 fontSize: 16,
 color: Colors.red,
 fontWeight: FontWeight.bold,
),
),
 SizedBox(
 height: 20,
),
 Middle()
],
);
}
}
class Middle extends StatelessWidget{
 const Middle({super.key});
 @override
 Widget build(BuildContext context) {
 return Column(
 children:[
 Text(
 'SpicyB is located at middle place',
 style: TextStyle(
 fontSize: 16,
),
),
 SizedBox(
 height: 20,
),
 SpicyB()
],
);
}
}
class SpicyB extends StatelessWidget{
 const SpicyB({super.key});
 @override
 Widget build(BuildContext context) {
 return Column(
 children:[
 Text(
 'Fish number : ${Provider.of<FishModel>(context).number}',
 style: TextStyle(
 fontSize: 16,
 color: Colors.red,
 fontWeight: FontWeight.bold,
),
),
 Text(
 'Fish size : ${Provider.of<FishModel>(context).size}',
 style: TextStyle(
 fontSize: 16,
 color: Colors.red,
 fontWeight: FontWeight.bold,
),
),
 SizedBox(
 height: 20,
),
 Low()
],
);
}
}
class Low extends StatelessWidget{
 const Low({super.key});
 @override
 Widget build(BuildContext context) {
 return Column(
 children:[
 Text(
 'SpicyC is located at low place',
 style: TextStyle(
 fontSize: 16,
),
),
 SizedBox(
 height: 20,
),
 SpicyC()
],
);
}
}
class SpicyC extends StatelessWidget{
 const SpicyC({super.key});
 @override
 Widget build(BuildContext context) {
 return Column(
 children:[
 Text(
 'Fish number : ${Provider.of<FishModel>(context).number}',
 style: TextStyle(
 fontSize: 16,
 color: Colors.red,
 fontWeight: FontWeight.bold,
),
),
 Text(
 'Fish size : ${Provider.of<FishModel>(context).size}',
 style: TextStyle(
 fontSize: 16,
 color: Colors.red,
 fontWeight: FontWeight.bold,
),
),
 SizedBox(
 height: 20,
),
],
);
}
}

fish_model.dart

class FishModel{
 final String name;
 final int number;
 final String size;
 FishModel({required this.name, required this.number, required this.size});
}



















[결과화면]






ChangeNotifier의 한계
1. 매번 수동으로 addListener를 등록해 주어야 함
2. 수동으로 addListener를 제거시켜 주어야 함
3. FishModel 인스턴스를 매번 생성자를 통해서 전달해야 함
4. UI 리빌드도 수동으로 해결해야 함

ChangeNotifierProvider의 장점
1. 모든 위젯들이listen할 수 있는 ChangeNotifier 인스턴스 생성
2. 자동으로 필요 없는 ChangeNotifier 제거
3. Provider.of를 통해서 위젯들이 쉽게 ChangeNotifier인스턴스에 접근할 수 있게 해줌
4. 필요시 UI를 리빌드 시켜줄 수 있음
5. 굳이 UI를 리빌드 할 필요가 없는 위젯을 위해서 listen: false 기능 제공




























