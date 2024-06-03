# FlutterStudy

[ const 없애는 방법 ]

pub spec.yaml - rules
prefer_const_literals_to_create_immutables : false 추가  

## AppBar
```
import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContextcontext) {

    return MaterialApp(

title:'YouJiWon',

home:MyHomePage(),

}

}

//home : 앱을 실행시켰을때 가장 먼저 보이는 경로지정

class MyHomePage extends StatelessWidget{

  const MyHomePage({super.key});

  @override

  Widget build(BuildContextcontext) {

    return Scaffold(

appBar:AppBar(

title:Text('유지원'),

centerTitle:true,

backgroundColor:Colors.red,

elevation:0.0,

),

body:Center(

child:Column(

children:[

            Text('Hello'),

            Text('1'),

            Text('2'),

],

),

),

}

}

//Scaffold : 빈 도화지, 위젯에 배치시키기 위해 사용된다.

//elevation : 앱바와 위젯 사이의 높이 지정으로 그림자를 의미한다.
```
 ![스크린샷 2023-08-20 154605](https://github.com/jiwon0629/FlutterStudy/assets/149983498/7fb55658-ba5c-422b-be20-855de3b41210)


 

결과



 

기초 위젯

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return MaterialApp(

      title:'YouJiWon',

      home:MyHomePage(),

      //home : 앱을 실행시켰을때 가장 먼저 보이는 경로지정

}

}

class MyHomePage extends StatelessWidget{

  const MyHomePage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      //Scaffold : 빈 도화지, 위젯에 배치시키기 위해 사용된다.

      appBar:AppBar(

        title:Text('유지원'),

        centerTitle:true,

        backgroundColor:Colors.red,

        elevation:0.0,

        //elevation : 앱바와 위젯 사이의 높이 지정으로 그림자를 의미한다.

),

      body:Center(

        child:Column(

          mainAxisAlignment:MainAxisAlignment.center,

          //mainAxisAlignment : 위젯들을 세로로 정렬시키기 위해 사용된다.

          children:[

            Text('Hello'),

            Text('Hello'),

            Text('Hello'),

],

),

),

}

}

 

결과



 

이미지 삽입 방법

1. New Folder로 폴더 생성 후 폴더에 이미지 삽입

2. pubspec.yaml에 들어가서 assets 부분 주석처리를 풀어준다.

3. 이미지 경로를 지정한 다음 저장한다.

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return const MaterialApp(

      debugShowCheckedModeBanner:false,//앱바에 있는 디버그 부분을 삭제

      title:'YouJiWon',

      home:MyHomePage(), //앱을 실행시켰을때 가장 먼저 보이는 경로지정

}

}

class MyHomePage extends StatelessWidget{

  const MyHomePage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

        //빈 도화지, 위젯에 배치시키기 위해 사용된다.

        //위젯 배경색 지정

        backgroundColor:Colors.amber[800],

        appBar:AppBar(

          title:const Text('유지원'),

          backgroundColor:Colors.amber[700],

          centerTitle:true,

          elevation:0.0, //앱바와 위젯 사이의 높이 지정으로 그림자를 의미한다.

),

        body:const Padding(

          padding:EdgeInsets.fromLTRB(30.0, 40.0, 0.0, 0.0),

          child:Column(

            crossAxisAlignment:CrossAxisAlignment.start, //가로 정렬

            children:[

              Divider(

                height:60.0, //divider 기준 위 아래 높이를 합쳐서 60임

                color:Colors.black,

                thickness:0.5, //선 굵기

                endIndent:30.0, //선의 끝 부분과 위젯과의 떨어지는 거리가 30

),

              Text(

                'Name',

                style:TextStyle(

                    color:Colors.white, letterSpacing:2.0 //text 간의 간격

),

),

              SizedBox(

                //name과 YouJiWon과의 간격을 만들기 위한 박스

                height:10.0,

),

              Text(

                'YouJiWon',

                style:TextStyle(

                    color:Colors.white,

                    letterSpacing:2.0,

                    fontSize:28.0,

                    fontWeight:FontWeight.bold),

),

              SizedBox(

                height:30.0,

),

              Text(

                'Level',

                style:TextStyle(

                    color:Colors.white, letterSpacing:2.0 //text 간의 간격

),

),

              SizedBox(

                //name과 YouJiWon과의 간격을 만들기 위한 박스

                height:10.0,

),

              Text(

                '14',

                style:TextStyle(

                    color:Colors.white,

                    letterSpacing:2.0,

                    fontSize:28.0,

                    fontWeight:FontWeight.bold),

),

              SizedBox(

                height:30.0,

),

              //가로 나열

              Row(

                children:[

                  Icon(Icons.check_circle_outline),

                  SizedBox(

                    width:10.0,

),

                  Text(

                    'ios',

                    style:TextStyle(fontSize:16.0, letterSpacing:1.0),

),

],

),

              //가로 나열

              Row(

                children:[

                  Icon(Icons.check_circle_outline),

                  SizedBox(

                    width:10.0,

),

                  Text(

                    'flutter',

                    style:TextStyle(fontSize:16.0, letterSpacing:1.0),

),

],

),

              //가로 나열

              Row(

                children:[

                  Icon(Icons.check_circle_outline),

                  SizedBox(

                    width:10.0,

),

                  Text(

                    'dart',

                    style:TextStyle(fontSize:16.0, letterSpacing:1.0),

),

],

),

],

),

));

}

}

 

 

결과



 

 

 

 

 

 

 

 

 

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return MaterialApp(

      debugShowCheckedModeBanner:false,

      title:'YouJiWon',

      theme:ThemeData(primarySwatch:Colors.red),

      home:MyHomePage(), //앱을 실행시켰을때 가장 먼저 보이는 경로지정

}

}

class MyHomePage extends StatelessWidget{

  const MyHomePage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      //Scaffold : 빈 도화지, 위젯에 배치시키기 위해 사용된다.

      appBar:AppBar(

        title:const Text('AppBar Icon Menu'),

        centerTitle:true,

        elevation:0.0, //앱바와 위젯 사이의 높이 지정으로 그림자를 의미한다.

       

        //메뉴아이콘

        leading://아이콘 버튼이나 간단한 위젯을 왼쪽에 배치할 때

            IconButton(

          icon:Icon(Icons.menu),

          onPressed:() {

            //함수의 형태로 일반 버튼이나 아이콘 버튼을 터치했을 때 일어나는 이벤트를 정의하는 곳

            print('menu button is clicked');

},

),

        //쇼핑카트, 검색 아이콘

        actions:[

          //복수의 아이콘 버튼 등을 오른쪽에 배치할 때

          IconButton(

            icon:Icon(Icons.shopping_cart),

            onPressed:() {

              print('shopping button is clicked');

},

),

          IconButton(

            icon:Icon(Icons.search),

            onPressed:() {

              print('search button is clicked');

},

),

],

),

}

}

 

 

결과



 

 

 

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return MaterialApp(

      debugShowCheckedModeBanner:false,

      title:'YouJiWon',

      theme:ThemeData(primarySwatch:Colors.red),

      home:MyHomePage(),

}

}

class MyHomePage extends StatelessWidget{

  const MyHomePage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      appBar:AppBar(

        title:const Text('AppBar Icon Menu'),

        centerTitle:true,

        elevation:0.0,

        //쇼핑카트, 검색 아이콘

        actions:[

          //actions : 복수의 아이콘 버튼 등을 오른쪽에 배치할 때

          IconButton(

            icon:const Icon(Icons.shopping_cart),

            onPressed:() {

              print('shopping button is clicked');

},

),

          IconButton(

            icon:const Icon(Icons.search),

            onPressed:() {

              print('search button is clicked');

},

),

],

),

      //메뉴화면

      drawer:Drawer(

        child:ListView(

          padding:EdgeInsets.zero,

          children:[

            //메뉴화면 정보 상단부분

            UserAccountsDrawerHeader(

              accountName:const Text('YouJiWon'),

              accountEmail:const Text('wjy_1116'),

              //화살표

              onDetailsPressed:() {

                print('arrow is clicked');

},

              //데코레이션

              decoration:const BoxDecoration(

                color:Colors.red,

                borderRadius:BorderRadius.only(

                  bottomLeft:Radius.circular(20.0),

                  bottomRight:Radius.circular(20.0),

),

),

),

            //메뉴화면 정보 하단부분

            ListTile(

              leading:Icon(

                Icons.home,

                color:Colors.grey[850],

),

              title:const Text('Home'),

              onTap:() {

                print('Home is clicked');

},

              trailing:Icon(Icons.add),

),

            ListTile(

              leading:Icon(

                Icons.settings,

                color:Colors.grey[850],

),

              title:const Text('Setting'),

              onTap:() {

                print('Settings is clicked');

},

              trailing:Icon(Icons.add),

),

            ListTile(

              leading:Icon(

                Icons.question_answer,

                color:Colors.grey[850],

),

              title:const Text('Q&A'),

              onTap:() {

                print('Q&A is clicked');

},

              trailing:Icon(Icons.add),

),

],

),

),

}

}

//currentAccountPicture : 현재 사용자의 이미지를 가져온다.

//otherAccountsPictures : 현재 사용자의 이미지와는 다른 사용자의 이미지를 가져온다.

//CircleAvatar : 원형 아바타(이미지)

 

결과



import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return const MaterialApp(

      debugShowCheckedModeBanner:false,

      title:'YouJiWon',

      home:MyHomePage(),

}

}

class MyHomePage extends StatelessWidget{

  const MyHomePage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      appBar:AppBar(

        title:const Text('Snack Bar'),

        centerTitle:true,

        backgroundColor:Colors.red,

),

      body:Builder(

        builder:(BuildContext ctx) {

          return Center(

            child:TextButton(

              //버튼 텍스트

              child:Text(

                'Show me',

                style:TextStyle(color:Colors.white),

),

              //버튼 배경색 지정

              style:const ButtonStyle(

                  backgroundColor:MaterialStatePropertyAll(Colors.red)),

              onPressed:() {

                ScaffoldMessenger.of(ctx).showSnackBar(

                  const SnackBar(

                    content:Text('Hello'),

),

);

},

),

);

},

),

}

}

 

결과



 

 

 

 

 

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return const MaterialApp(

      debugShowCheckedModeBanner:false,

      title:'YouJiWon',

      home:MyHomePage(),

}

}

class MyHomePage extends StatelessWidget{

  const MyHomePage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      appBar:AppBar(

        title:Text('Snack Bar'),

        centerTitle:true,

),

      body:MySnackBar(),

}

}

class MySnackBar extends StatelessWidget{

  const MySnackBar({super.key});

  @override

  Widget build(BuildContext context) {

    return Center(

      child:ElevatedButton(

        child:Text('Show me'),

        onPressed:() {

          ScaffoldMessenger.of(context).showSnackBar(

            SnackBar(

              content:Text(

                'Hello',

                textAlign:TextAlign.center,

                style:TextStyle(color:Colors.white),

),

              backgroundColor:Colors.teal,

              duration:Duration(milliseconds:1000),

),

);

},

),

}

}

 

 

결과



 

 

 

 

 

 

 

 

 

 

 

 

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return const MaterialApp(

      debugShowCheckedModeBanner:false,

      title:'YouJiWon',

      home:MyPage(),

}

}

class MyPage extends StatelessWidget{

  const MyPage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      backgroundColor:Colors.blue,

      body:SafeArea(

        child:Container(

          color:Colors.red,

          width:100,

          height:100,

          margin:EdgeInsets.symmetric(vertical:80, horizontal:20),

          padding:EdgeInsets.all(40),

          child:Text('Hello'),

),

),

}

}

//EdgeInserts.all(value) : valud만큼 높이 너비 지정

//EdgeInserts.symmetric(vertical : 80, horizontal) : 80만큼 높이, 20만큼 너비 지정

//margin : 컨테이너가 스크린의 가장자리에서 일정 간격을 가지게 하기위해서 사용

//padding : 컨테이너가 포함하고 있는 요소가 가장자리에서 일정 간격을 가지게 하기위해서 사용

 

 

 

결과



 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

 

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return const MaterialApp(

      debugShowCheckedModeBanner:false,

      title:'YouJiWon',

      home:MyPage(),

}

}

class MyPage extends StatelessWidget{

  const MyPage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      backgroundColor:Colors.teal,

      body:SafeArea(

        child:Column(

          crossAxisAlignment:CrossAxisAlignment.stretch,//화면 꽉 채움

          children:[

            Container(

              width:100,

              height:100,

              color:Colors.white,

              child:const Text('Container 1'),

),

            Container(

              width:100,

              height:100,

              color:Colors.blue,

              child:const Text('Container 2'),

),

            Container(

              width:100,

              height:100,

              color:Colors.red,

              child:const Text('Container 3'),

),

            // Container(

            //   width: double.infinity,//가로축 끝까지 붙이기 위함

            // )

],

),

),

}

}

//mainAxisAlignment : 세로축 위치 담당

//mainAxisSize : 세로출 공간 담당

//crossAxisAlignment : 가로축 위치 담당

 

결과



 

 

 

화면 이동은 스택구조와 같다. 첫 화면에서 다른 화면으로 push처럼 위로 쌓여져 올라간다.

pop도 다른 화면이 빠져나가서 첫 화면이 나타난다.

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return const MaterialApp(

      debugShowCheckedModeBanner:false,

      title:'YouJiWon',

      home:FirstPage(),

}

}

class FirstPage extends StatelessWidget{

  const FirstPage({super.key});

  @override

  Widget build(BuildContext context1) {

    return Scaffold(

      appBar:AppBar(

        title:Text('First page'),

),

      body:Center(

        child:ElevatedButton(

          onPressed:() {

            Navigator.push(

              context1,

              MaterialPageRoute(

                builder:(context) =>SecondPage(),

),

);

},

          child:Text('Go to the Second page'),

),

       

       

),

     

}

}

class SecondPage extends StatelessWidget{

  const SecondPage({super.key});

  @override

  Widget build(BuildContext context2) {

    return Scaffold(

      appBar:AppBar(

        title:Text('Second page'),

),

      body:Center(

        child:ElevatedButton(

          onPressed:() {

            Navigator.pop(context2);

},

          child:Text('Go to the First page'),

),

),

}

}

화면 이동 전 결과

 



 

화면 이동 후 결과



 

Map 자료구조

Key : Value

String : Widget builder

 

Interpolation : 보간법

ex) 당신의 점수는 $score 이며 당신의 레벨은 $level입니다.

 

Collection : 데이터들을 모아서 가지고 있는 자료구조

Generic : Collection이 가지고 있는 데이터들의 데이터 타입을 지정

 

 

 

 

 

 

 

 

 

 

import 'package:flutter/material.dart';

void main() =>runApp(const MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return const MaterialApp(

      debugShowCheckedModeBanner:false,

      title:'YouJiWon',

      home:MyPage(),

}

}

class MyPage extends StatelessWidget{

  const MyPage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      appBar:AppBar(

        title:const Text('Scaffold Messenger'),

),

      body:const HomeBody(),

      floatingActionButton:FloatingActionButton(

        onPressed:() {

          ScaffoldMessenger.of(context).showSnackBar(

            SnackBar(

              content:const Text('Like a new Snack bar!'),

              duration:const Duration(seconds:5), //지속시간

              action:SnackBarAction(

                label:'Undo',

                onPressed:() {

                  Navigator.push(

                    context,

                    MaterialPageRoute(builder:(context) =>const ThirdPage()),

);

},

),

),

);

},

        child:const Icon(Icons.thumb_up),

),

}

}

class HomeBody extends StatelessWidget{

  const HomeBody({super.key});

  @override

  Widget build(BuildContext context) {

    return Center(

        child:ElevatedButton(

            onPressed:() {

              Navigator.push(

                context,

                MaterialPageRoute(builder:(context) =>const SecondPage()),

);

},

            child:const Text('Go to the second page')));

}

}

class SecondPage extends StatelessWidget{

  const SecondPage({super.key});

  @override

  Widget build(BuildContext context) {

    return Scaffold(

      appBar:AppBar(

        title:const Text('Second Page'),

),

      body:const Center(

        child:Text(

          '"좋아요가 추가 되었습니다."',

          style:TextStyle(fontSize:20.0, color:Colors.redAccent),

),

),

}

}

class ThirdPage extends StatelessWidget{

  const ThirdPage({super.key});

  @override

  Widget build(BuildContext context) {

    return ScaffoldMessenger(

      child:Scaffold(

        appBar:AppBar(

          title:const Text('Third Page'),

),

        body:Builder(builder:(context) {

          return Center(

            child:Column(

              mainAxisAlignment:MainAxisAlignment.center,

              children:[

                const Text(

                  '"좋아요"를 취소 하시겠습니까?',

                  style:TextStyle(fontSize:20.0, color:Colors.redAccent),

),

                ElevatedButton(

                  onPressed:() {

                    ScaffoldMessenger.of(context).showSnackBar(

                      const SnackBar(

                        content:Text('"좋아요"가 취소되었습니다.'),

                        duration:Duration(seconds:3),

),

);

},

                  child:const Text('취소하기'),

),

],

),

);

}),

),

}

}

 

 

 

 

 

 

결과



 

 

import 'package:flutter/material.dart';

void main() =>runApp(const MyApp());

class MyApp extends StatelessWidget{

  const MyApp({super.key});

  @override

  Widget build(BuildContext context) {

    return const MaterialApp(

      debugShowCheckedModeBanner:false,

      home:ListViewPage(),

}

}

class ListViewPage extends StatefulWidget{

  const ListViewPage({super.key});

  @override

  State<ListViewPage> createState() =>_ListViewPageState();

}

class _ListViewPageState extends State<ListViewPage> {

  var titleList =['Dentist', 'Pharmacist', 'School teacher', 'IT manager'];

  var description =['1. aa', '2.bb', '3.cc', '4.dd', '5.ee'];

  void showPopup(context, title, description) {

    showDialog(

      context:context,

      builder:(context) {

        return Dialog(

          child:Container(

            width:MediaQuery.of(context).size.width *0.7,

            height:380,

            decoration:BoxDecoration(

                borderRadius:BorderRadius.circular(10), color:Colors.white),

            child:Column(

              children:[

                ClipRRect(

                  //이미지를 사각형 모양으로 출력

                  borderRadius:BorderRadius.circular(10),

),

                const SizedBox(

                  height:10,

),

                Text(

                  title,

                  style:const TextStyle(

                      fontSize:25,

                      fontWeight:FontWeight.bold,

                      color:Colors.grey),

),

                Padding(

                  padding:const EdgeInsets.all(8),

                  child:Text(

                    description,

                    maxLines:3, //description 데이터가 최대 몇 줄까지 보여줄 것인지

                    style:const TextStyle(fontSize:15, color:Colors.grey),

                    textAlign:TextAlign.center,

),

),

                ElevatedButton.icon(

                  onPressed:() {

                    Navigator.pop(context);

},

                  icon:const Icon(Icons.close),

                  label:const Text('close'),

),

],

),

),

);

},

}

  @override

  Widget build(BuildContext context) {

    //화면이 가로모드가 되었을때 일정한 배치가 유지되어야하므로

    //description은 반응형으로 만들어준다.

    //화면이 바뀔때마다 재배치 되어야 하기 때문이다.

    //가로모드가 되었을때 description 데이터가 디바이스 전체 너비의 60%를 차지한다.

    double width =MediaQuery.of(context).size.width *0.6;

    return Scaffold(

      appBar:AppBar(

        backgroundColor:Colors.white,

        elevation:0,

        title:const Text(

          'ListView',

          style:TextStyle(color:Colors.grey),

),

),

      body:ListView.builder(

        itemCount:titleList.length,

        itemBuilder:(context, index) {

          return GestureDetector(

            //터치에 반응하는 제스쳐 기능을 사용하기 위해 사용

            onTap:() {

              debugPrint(titleList[index]);

              showPopup(context, titleList[index], description[index]);

},

            child:Card(

              child:Row(

                children:[

                  const SizedBox(

                    width:100,

                    height:100,

),

                  Padding(

                    padding:const EdgeInsets.all(10),

                    child:Column(

                      children:[

                        Text(

                          titleList[index],

                          style:const TextStyle(

                              fontSize:22,

                              fontWeight:FontWeight.bold,

                              color:Colors.grey),

),

                        const SizedBox(

                          height:10,

),

                        SizedBox(

                          width:width,

                          child:Text(

                            description[index],

                            style:const TextStyle(

                                fontSize:15, color:Colors.grey),

),

)

],

),

),

],

),

),

);

},

),

}

}

 

 

결과



 

ListView VS ListView.builder

공통점

- 스크롤이 가능한 배열형 위젯

2. 차이점

ListView : 리스트뷰안에 모든 차일드를 생성해서 보여줌

Listview.builder : 그때그때 필요한만큼만 데이터를 저장소나 서버에서 불러옴

 

약간 매운맛===================================================================

 

State

State란 UI가 변경되도록 영향을 미치는 데이터이다.

App 수준과 Widget 수준의 데이터가 있다.

 

Stateless Widget

Stateless widget : State가 변하지 않는 위젯

 

 

 

 

Widget tree and Element tree

Widget tree는 빌드 메소드가 호출될 때마다 새롭게 rebuild된다.

Reload는 어떤 프레임을 그대로 둔 채 부수적인 요소들만 바꾸는 것

Rebuild는 새로 만드는 것

Stateless 위젯은 rebuild만을 통해서 State 적용 가능

 

Extend(상속)

상속을 사용하는 이유는 자원을 재사용하고 자원을 변형하거나 추가하는 역할

부모 클래스가 갖고 있는 속성기능들을 상속받은 자식클래스는 추가없이 부모 클래스의 모든 것을 그대로 사용가능하고 원하는대로 변형할 수 있다.

 

부모 클래스의 생성자가 먼저 호출되고 자식 클래스의 생성자가 다음에 호출된다.

 

Stateful Widget은 내부에 State라는 또 다른 클래스를 갖고 있다.

 

Stateful Widget이 rebuild되는 경우

Stateless Widget처럼 Child 위젯의 생성자를 통해서 데이터가 전달 때

Internal state가 바뀔 때

 

import 'package:flutter/material.dart';

void main() =>runApp(MyApp());

class MyApp extends StatefulWidget{

  @override

  State<MyApp> createState() =>_MyAppState();

}

class _MyAppState extends State<MyApp> {

  int counter =0;

  @override

  Widget build(BuildContext context) {

    return MaterialApp(

      debugShowCheckedModeBanner:false,

      theme:ThemeData(primarySwatch:Colors.blue),

      home:Scaffold(

        appBar:AppBar(),

        body:Center(

          child:Column(

            mainAxisAlignment:MainAxisAlignment.center,

            children:[

              const Text('You :'),

              Text(

                '$counter',

                style:Theme.of(context).textTheme.displayMedium,

),

],

),

),

        floatingActionButton:FloatingActionButton(

          child:const Icon(Icons.add),

          onPressed:() {

            setState(() {

              counter++;

              print("$counter");

});

},

),

),

}

}

 

 

결과

