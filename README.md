# async-and-future-code


void main() {
  print('Generate Number');
  Stream<int> numbers = getNumbers(6);
  print('listening Number');
  numbers.listen((int value) {
    print('$value');
  });
  print("end of main");
}

Stream<int> getNumbers(int number) async* {
  print('waiting inside generator a bit');
  await new Future.delayed(new Duration(seconds: 8));
  print('started generating values...');
  for (int i = 0; i < number; i++) {
    await new Future.delayed(new Duration(seconds: 1));
    yield i;
  }
  print('ended generating values...');
}
