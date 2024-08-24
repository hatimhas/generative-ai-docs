For an interactive experience, use the following DartPad.
Use the numbered horizontal scrolling bar to switch between
29 different examples.
code-excerpt "lib/main.dart"?
```dartpad title="Constraints DartPad hands-on example" run="true"
import 'package:flutter/material.dart';
void main() => runApp(const HomePage());
const red = Colors.red;
const green = Colors.green;
const blue = Colors.blue;
const big = TextStyle(fontSize: 30);
//////////////////////////////////////////////////
class HomePage extends StatelessWidget {
  const HomePage();
@override
  Widget build(BuildContext context) {
    return const FlutterLayoutArticle([
      Example1(),
      Example2(),
      Example3(),
      Example4(),
      Example5(),
      Example6(),
      Example7(),
      Example8(),
      Example9(),
      Example10(),
      Example11(),
      Example12(),
      Example13(),
      Example14(),
      Example15(),
      Example16(),
      Example17(),
      Example18(),
      Example19(),
      Example20(),
      Example21(),
      Example22(),
      Example23(),
      Example24(),
      Example25(),
      Example26(),
      Example27(),
      Example28(),
      Example29(),
    ]);
  }
}
//////////////////////////////////////////////////
abstract class Example extends StatelessWidget {
  const Example();
String get code;
String get explanation;
}
//////////////////////////////////////////////////
class FlutterLayoutArticle extends StatefulWidget {
  const FlutterLayoutArticle(
    this.examples, {
    super.key,
  });
final List examples;
@override
  State createState() => _FlutterLayoutArticleState();
}
//////////////////////////////////////////////////
class _FlutterLayoutArticleState extends State {
  late int count;
  late Widget example;
  late String code;
  late String explanation;
@override
  void initState() {
    count = 1;
    code = const Example1().code;
    explanation = const Example1().explanation;
super.initState();
}
@override
  void didUpdateWidget(FlutterLayoutArticle oldWidget) {
    super.didUpdateWidget(oldWidget);
    var example = widget.examples[count - 1];
    code = example.code;
    explanation = example.explanation;
  }
@override
  Widget build(BuildContext context) {
    return MaterialApp(
      debugShowCheckedModeBanner: false,
      title: 'Flutter Layout Article',
      home: SafeArea(
        child: Material(
          color: Colors.black,
          child: FittedBox(
            child: Container(
              width: 400,
              height: 670,
              color: const Color(0xFFCCCCCC),
              child: Column(
                crossAxisAlignment: CrossAxisAlignment.center,
                children: [
                  Expanded(
                      child: ConstrainedBox(
                          constraints: const BoxConstraints.tightFor(
                              width: double.infinity, height: double.infinity),
                          child: widget.examples[count - 1])),
                  Container(
                    height: 50,
                    width: double.infinity,
                    color: Colors.black,
                    child: SingleChildScrollView(
                      scrollDirection: Axis.horizontal,
                      child: Row(
                        mainAxisSize: MainAxisSize.min,
                        children: [
                          for (int i = 0; i < widget.examples.length; i++)
                            Container(
                              width: 58,
                              padding: const EdgeInsets.only(left: 4, right: 4),
                              child: button(i + 1),
                            ),
                        ],
