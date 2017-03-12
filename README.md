# [Android] AnimatedGifEncoder
#### Un codificador GIF animado para Android
======

@see https://github.com/nbadal/android-gif-encoder



## Código de ejemplo

    ByteArrayOutputStream bos = new ByteArrayOutputStream();
    AnimatedGifEncoder encoder = new AnimatedGifEncoder();
    encoder.setDelay(500);  // ディレイ 500/ms
    encoder.setRepeat(0);   // 0:ループする -1:ループしない
    encoder.start(bos);     // gitデータ生成先ををbosに設定

    try {
      Bitmap bmp1, bmp2, bmp3;

      // ファイルの読み込み
      bmp1 = BitmapFactory.decodeStream(new FileInputStream("/sdcard/target1.png"));
      encoder.addFrame(bmp1);  // gifに追加
      bmp1.recycle();

      bmp2 = BitmapFactory.decodeStream(new FileInputStream("/sdcard/target2.png"));
      encoder.addFrame(bmp2);  // gifに追加
      bmp2.recycle();
    
      bmp3= BitmapFactory.decodeStream(new FileInputStream("/sdcard/target3.png"));
      encoder.addFrame(bmp3);  // gifに追加
      bmp3.recycle();

    } catch (FileNotFoundException e) {
    }

    encoder.finish();  // 終了

    File filePath = new File("/sdcard", "sample.gif");
    FileOutputStream outputStream;
    try {
      outputStream = new FileOutputStream(filePath);
      // bosに生成されたgifデータをファイルに吐き出す
      outputStream.write(bos.toByteArray());
    } catch (FileNotFoundException e) {
    } catch (IOException e) {
    }
