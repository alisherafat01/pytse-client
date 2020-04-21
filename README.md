# pyTSEClient (python tse client)
&rlm;
با استفاده از این پکیج میتونید به دیتای بازار بورس تهران در پایتون دسترسی داشته باشید.
&rlm;

&rlm;
هدف حل مشکلات گرفتن اطلاعات بروز از سایت بازار بورس تهران هست.
&rlm;

## قابلیت ها
 * دریافت اطلاعات روز های معاملاتی هر سهم و قابلیت ذخیره سازی
 * قابلیت گرفتن اطلاعات یک سهام

## نصب 
```bash
pip install pytse-client 
```

## نحوه استفاده
### دانلود سابقه سهم ها
با استفاده از این تابع میتوان سابقه سهام هارو دریافت کرد و هم اون رو ذخیره و هم توی کد استفاده کرد
```python
import pytse_client as tse
tickers = tse.download(symbols="all", write_to_csv=True)
tickers["ولملت"] # history

            date     open     high  ...     volume  count    close
0     2009-02-18   1050.0   1050.0  ...  330851245    800   1050.0
1     2009-02-21   1051.0   1076.0  ...  335334212   6457   1057.0
2     2009-02-22   1065.0   1074.0  ...    8435464    603   1055.0
3     2009-02-23   1066.0   1067.0  ...    8570222    937   1060.0
4     2009-02-25   1061.0   1064.0  ...    7434309    616   1060.0
...          ...      ...      ...  ...        ...    ...      ...
2323  2020-04-14   9322.0   9551.0  ...  105551315  13536   9400.0
2324  2020-04-15   9410.0   9815.0  ...  201457026  11322   9815.0
2325  2020-04-18  10283.0  10283.0  ...  142377245   8929  10283.0
2326  2020-04-19  10797.0  10797.0  ...  292985635  22208  10380.0
2327  2020-04-20  10600.0  11268.0  ...  295590437  16313  11268.0
```
سابقه سهم توی فایلی با اسم سهم نوشته میشه `write_to_csv=True` همچنین با گذاشتن

است `Dataframe` سابقه سهم در قالب


برای دانلود سابقه یک یا چند سهم کافی هست اسم اون ها به تابع داده بشه:
```python
import pytse_client as tse
tse.download(symbols="وبملت", write_to_csv=True)
tse.download(symbols=["وبملت", "ولملت"], write_to_csv=True)
```

### Ticker ماژول
&rlm;
این ماژول به شما اجازه میده در پایتون به اطلاعات سهام دسترسی داشته باشید.
برای مثال:
&rlm;
```python
import pytse_client as tse

tse.download(symbols="وبملت", write_to_csv=True)  # optional
ticker = tse.Ticker("وبملت")

# سابقه
ticker.history

# آدرس سهم
ticker.url

# آیدی سهم در سایت
ticker.index

```
برای استفاده لازم نیست حتما تابع دانلود صدا زده بشه.
اگر این کد رو بدون دانلود کردن سهم  استفاده کنید خودش اطلاعات سهم رو از سایت میگیره،
اما اگر قبل از اون از دانلود استفاده کرده باشید
به جای گرفتن از اینترنت اطلاعات رو از روی فایل میخونه که سریع تر هست

##### نکته
&rlm;
طبق تجربه‌ ای که داشتم چون گاهی اوقات سایت بورس مدت زیادی طول میکشه تا اطلاعات رو بفرسته یا بعضی مواقع نمیفرسته بهتر هست که اول تابع دانلود رو استفاده کنید برای سهم هایی که لازم هست و بعد با دیتای اون ها کار کنید.
&rlm;
#### &rlm; پکیج های مورد نیاز: &rlm; 
* [Pandas](https://github.com/pydata/pandas)
* [Requests](http://docs.python-requests.org/en/master/)
#### &rlm; الهام گرفته از: &rlm; 
* tehran_stocks: https://github.com/ghodsizadeh/tehran-stocks
* yfinance: https://github.com/ranaroussi/yfinance