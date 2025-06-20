# java-libs

## 此專案包含以下共用元件:
1. Big5Helper: 支援 Big5 字碼與字元轉換
2. UnicodeHelper: 支援 UTF-8 字碼與字元轉換
3. AesHelper: 支援 AES256(ECB模式) 加解密
4. AesCBCHelper: 支援 AES256(CBC模式) 加解密
5. CDateHelper: 使用 time4j 實作國曆與農曆日期互轉


## 使用說明:

> 專案使用前需引用 jcore-1.6.jar, jcore-enc-1.6.jar

### 1.Big5, UTF-8 字碼與字元轉換(含難字)
//big5, utf-8 轉碼
String big5Char = "常";

String big5Code = Big5Helper.getCode(big5Char);

String utf8Char = UnicodeHelper.big5ToUtf8String(big5Char);

String utf8Code = UnicodeHelper.stringToUtf8(utf8Char);

### 2.AES 加解密
AesHelper.setSecKey("1234");

//AesHelper.setKeyLength(KeyLength.KEY128);

String plainText="hello";	

String encryptedText = AesHelper.encrypt(plainText);

String decryptedText = AesHelper.decrypt(encryptedText);

### 3.使用 time4j 實作國曆與農曆日期互轉
> 專案使用前需再引用 tim4j 相關 jar 檔

LogHelper.v(TAG, "轉成國曆: " +CDateHelper.getGregorianDateString("2023", "2", "15"));

LogHelper.v(TAG, "轉成農曆: " + CDateHelper.getChineseDateString(2023, 4, 5));//農曆潤2月

LogHelper.v(TAG, "農曆當月初一: " + CDateHelper.getChineseCurrentMonthDay("1"));

LogHelper.v(TAG, "農曆當月月底: " + CDateHelper.getChineseCurrentMonthLastDay());

Date baseDate = CDateHelper.getDate("2023-03-22");

LogHelper.v(TAG, "農曆下月初一: " + DateHelper.getDateString(CDateHelper.getChineseNextMonthDay(baseDate,"1").toDate()));

LogHelper.v(TAG, "農曆下月月底: " + CDateHelper.getChineseNextMonthLastDay(baseDate));

baseDate = CDateHelper.getDate("2023-01-22");

LogHelper.v(TAG, "農曆明年大年初一: " + CDateHelper.getChineseNextYearDay(baseDate,"1","1"));

LogHelper.v(TAG, "冬至: " + CDateHelper.getWinterSolsticeDate(2023));

