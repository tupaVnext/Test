flutter config --jdk-dir "/Users/****/Library/Java/JavaVirtualMachines/corretto-17.0.13/Contents/Home"

| 20240330120713000028  | 0 nft
| 20240402150409000117  |  1 nft
| 20240402154431000118  | 8 nft
| 20240402170415000126  | 9 nft
| 20240405105131000236  | 10 nft
| 20240406152608000278  |  20 nft
| 20240406183303000283  | 50 nft 
| 20240407113723000284  | 0 nft
| 20240408115539000301  | 0 nft


const String A = 'hello';
const String B = 'world';
String C = 'This is a hello message.';

final pattern = RegExp('(${RegExp.escape(A)}|${RegExp.escape(B)})');

if (C.contains(pattern)) {
  print('Chuỗi C có chứa A hoặc B');
} else {
  print('Chuỗi C không chứa A hoặc B');
}
