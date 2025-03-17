flutter config --jdk-dir "/Users/cuongdt/Library/Java/JavaVirtualMachines/corretto-17.0.13/Contents/Home"

class TrianglePainter extends CustomPainter {
  @override
  void paint(Canvas canvas, Size size) {
    Paint paint = Paint()
      ..color = Colors.white
      ..style = PaintingStyle.fill;

    Path path = Path()
      ..moveTo(size.width, size.height)
      ..lineTo(size.width, 0)
      ..lineTo(0, 0)
      ..close();

    canvas.drawPath(path, paint);

    Paint shadowPaint = Paint()
      ..color = Colors.black.withOpacity(0.17)
      ..maskFilter = const MaskFilter.blur(BlurStyle.inner, 10);

    canvas.drawPath(path.shift(Offset(-6.w, 3.w)), shadowPaint);

    final textPainter = TextPainter(
      text: TextSpan(
        text: 'text',
        style:
            AppTextStyle.semiBoldHiragino_10.copyWith(letterSpacing: 10 * 0.04),
      ),
      textDirection: TextDirection.ltr,
    );

    textPainter.layout();
    final double centerX = size.width / 2 + 10.w;
    final double centerY = size.height / 2 - 8.w;

    canvas.save();
    canvas.translate(centerX, centerY);
    canvas.rotate(pi / 4);

    textPainter.paint(
        canvas, Offset(-textPainter.width / 2, -textPainter.height / 2));
    canvas.restore();
  }

  @override
  bool shouldRepaint(CustomPainter oldDelegate) => false;
}

class TriangleWidget extends StatelessWidget {
  const TriangleWidget({super.key});

  @override
  Widget build(BuildContext context) {
    return CustomPaint(
      size: const Size(57, 57),
      painter: TrianglePainter(),
    );
  }
}
