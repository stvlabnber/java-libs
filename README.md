# java-libs

## 此專案包含以下共用元件:
1. Big5Helper: 支援 Big5 字碼與字元轉換
2. UnicodeHelper: 支援 UTF-8 字碼與字元轉換
3. AesHelper: 支援 AES256(ECB模式) 加解密
4. AesCBCHelper: 支援 AES256(CBC模式) 加解密


## 使用說明:

引用 jcore-1.6.jar, jcore-enc-1.6.jar

### 1.Big5, UTF-8 字元系統的字碼與字元轉換(含難字)
//big5, utf-8 轉碼
String big5Char = "常";

String big5Code = Big5Helper.getCode(big5Char);

String utf8Char = UnicodeHelper.big5ToUtf8String(big5Char);

String utf8Code = UnicodeHelper.stringToUtf8(utf8Char);

### 2.AES256 加解密
AesHelper.setSecKey("1234");
//AesHelper.setKeyLength(KeyLength.KEY128);

String plainText="hello";	

String encryptedText = AesHelper.encrypt(plainText);

String decryptedText = AesHelper.decrypt(encryptedText);
