```php、
/**
 * @link https://www.php.net/manual/zh/function.gmdate
 */
$format = "Y-m-d\TH:i:s\Z";
echo date($format);
echo "\r";

echo gmdate($format);
echo "\r";

date_default_timezone_set("GMT");
echo date($format);
die;

//输出结果
2020-06-03T14:57:53Z
2020-06-03T06:57:53Z
2020-06-03T06:57:53Z

```


```php
    /**
     * 格式化UTC时间为字符串
     * @param UTCDateTime|null $utcDateTime
     * @param string      $format
     *
     * @return string
     */

    public function formatUtcDateTimeToStr($utcDateTime,$format = "Y-m-d H:i:s")
    {
        if($utcDateTime instanceof UTCDateTime){
            return $utcDateTime->toDateTime()
                ->setTimezone(new \DateTimeZone('Asia/Shanghai'))
                ->format($format);
        }
        return "";
    }

    /**
     * 生成UTC时间类
     * @param string $dateTimeStr
     *
     * @return UTCDateTime
     */
    public function formatDateTimeToUtc($dateTimeStr = "now")
    {
        $dateTime = new \DateTime($dateTimeStr,new \DateTimeZone('Asia/Shanghai'));
        return new UTCDateTime($dateTime);
    }

```
