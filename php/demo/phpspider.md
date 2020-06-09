```php
error_reporting(-1);
define("ROOT",__DIR__);
define("LOCAL",dirname(ROOT));
define("VENDOR",LOCAL.DIRECTORY_SEPARATOR."vendor");

include_once VENDOR.DIRECTORY_SEPARATOR."autoload.php";
// http://bank.jrj.com.cn/bankpro/data.shtml
use phpspider\core\requests;
use phpspider\core\selector;
use phpspider\core\phpspider;
//
// $res = requests::get('http://bankpro.jrj.com.cn/json/f.jspa?size=20&pn=2&t={"st":"0","xsdq":"-1,-1","sort":"sell_org_date","order":"desc","wd":""}');
// $jsonStr = str_replace("var bps=","",$res);
// $lists = json_decode($jsonStr,true);

/* Do NOT delete this comment */
/* 不要删除这段注释 */

// $html = requests::get("http://bank.jrj.com.cn/bankpro/product/130550208/");
// var_dump(selector::select($html,"/html/body/div[9]/div/div[1]/div[3]/div/table/"));
// var_dump(selector::select($html,"/html/body/div[9]/div/div[1]/div[3]/div/table/tr[1]/td[2]"));
// var_dump(selector::select($html,"/html/body/div[9]/div/div[1]/div[2]/div/table/tr[3]/td[4]/i"));
// die;
$configs = array(
    'name' => '金融街',
    'log_file' => './log/jrj.log',
    'log_show'=>false,
    'domains' => array(
        'jrj.com.cn',
        'bankpro.jrj.com.cn',
        'bank.jrj.com.cn'
    ),
    'scan_urls' => array(
        'http://bank.jrj.com.cn/bankpro/data.shtml'
    ),
    'content_url_regexes' => array(
        "http://bank.jrj.com.cn/bankpro/product/\d+",
    ),
    'list_url_regexes' => array(
        'http://bankpro.jrj.com.cn/json/f.jspa\?size=20&pn=\d+&t={"st":"0","xsdq":"-1,-1","sort":"sell_org_date","order":"desc","wd":""}'
    ),
    // 'interval'=>1000,
    'export' => array(
        'type' => 'csv',
        'file' => './data/jrj.csv',
    ),
    'user_agent' => array(
        phpspider::AGENT_ANDROID, phpspider::AGENT_PC,phpspider::AGENT_IOS,
    ),
    'fields' => array(
        [
            'name' => "sp_prd_list_info",
            // 在内容页中通过XPath提取列表数据
            'selector' => "//a[contains(@class,'sp_prd_list_info')]",
            'required' => true,
        ],
        [
            'name'=>'综合评级',
            'selector'=>'/html/body/div[9]/div/div[1]/div[2]/div/table/tr[2]/td[2]/i',
        ],
        [
            'name'=>'收益性评级',
            'selector'=>'/html/body/div[9]/div/div[1]/div[2]/div/table/tr[3]/td[2]/i',
        ],
        [
            'name'=>'安全性评级',
            'selector'=>'/html/body/div[9]/div/div[1]/div[2]/div/table/tr[3]/td[4]/i',
        ],
        [
            'name'=>'流动性评级',
            'selector'=>'/html/body/div[9]/div/div[1]/div[2]/div/table/tr[3]/td[6]/i',
        ],
        [
            'name'=>'发行银行',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[1]/td[2]',
        ],
        [
            'name'=>'发行对象',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[1]/td[4]',
        ],
        [
            'name'=>'货币币种',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[1]/td[6]',
        ],
        [
            'name'=>'投资类型',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[2]/td[2]',
        ],
        [
            'name'=>'发行起始日期',
            'selector'=>'//*[@id="sell_org_date"]',
        ],
        [
            'name'=>'发行终止日期',
            'selector'=>'//*[@id="sell_end_date"]',
        ],
        [
            'name'=>'委托管理期限',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[3]/td[2]',
        ],
        [
            'name'=>'委托币种起始金额',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[3]/td[4]',
        ],
        [
            'name'=>'起购金额递增单位',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[3]/td[6]',
        ],
        [
            'name'=>'可否质押贷款',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[4]/td[2]',
        ],
        [
            'name'=>'银行是否可提前终止',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[4]/td[4]',
        ],
        [
            'name'=>'客户是否可赎回',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[4]/td[6]',
        ],
        [
            'name'=>'销售地区',
            'selector'=>'/html/body/div[9]/div/div[1]/div[3]/div/table/tr[5]/td[2]/span',
        ],
        [
            'name'=>'收益类型',
            'selector'=>'/html/body/div[9]/div/div[1]/div[4]/div/table/tr[1]/td[2]',
        ],
        [
            'name'=>'预期最高收益率',
            'selector'=>'/html/body/div[9]/div/div[1]/div[4]/div/table/tr[1]/td[4]',
        ],
        [
            'name'=>'到期最高收益率',
            'selector'=>'/html/body/div[9]/div/div[1]/div[4]/div/table/tr[1]/td[6]',
        ],
        [
            'name'=>'与同期储蓄比',
            'selector'=>'/html/body/div[9]/div/div[1]/div[4]/div/table/tr[2]/td[2]',
        ],
        [
            'name'=>'收益起始日期',
            'selector'=>'/html/body/div[9]/div/div[1]/div[4]/div/table/tr[2]/td[4]',
        ],
        [
            'name'=>'收益终止日期',
            'selector'=>'/html/body/div[9]/div/div[1]/div[4]/div/table/tr[2]/td[6]',
        ],
        [
            'name'=>'收益率说明',
            'selector'=>'/html/body/div[9]/div/div[1]/div[7]/div/table/tr[1]/td[2]',
        ],
        [
            'name'=>'申购条件说明',
            'selector'=>'/html/body/div[9]/div/div[1]/div[7]/div/table/tr[2]/td[2]',
        ],
        [
            'name'=>'银行提前终止条件',
            'selector'=>'/html/body/div[9]/div/div[1]/div[7]/div/table/tr[3]/td[2]',
        ],
        [
            'name'=>'赎回规定说明',
            'selector'=>'/html/body/div[9]/div/div[1]/div[7]/div/table/tr[4]/td[2]',
        ],
        [
            'name'=>'投资风险说明',
            'selector'=>'/html/body/div[9]/div/div[1]/div[7]/div/table/tr[5]/td[2]',
        ],
    ),
);

$spider = new \phpspider\core\phpspider($configs);
//获取到scan页后
$spider->on_scan_page = function($page, $content, $phpspider)
{
    // 生成列表页URL入队列
    for ($i = 1; $i <= 10; $i++)
    {
        $url = 'http://bankpro.jrj.com.cn/json/f.jspa?size=20&pn='.$i.'&t={"st":"0","xsdq":"-1,-1","sort":"sell_org_date","order":"desc","wd":""}';
        $phpspider->add_url($url);
    }
    // 通知爬虫不再从当前网页中发现待爬url
    return false;
};
/*
//页面加载完成后
$spider->on_download_page = function($page, $phpspider)
{
    if(($phpspider->is_list_page($page['url']))){
        $page['raw'] = "<html><body>".str_replace("var bps=","",$page['raw'])."</body></html>";
        // $page['raw'] = json_decode($page['raw'],true);
    }
    return $page;
};*/
//获取到列表页后
$spider->on_list_page = function($page, $content, $phpspider)
{
    // 在列表页中通过XPath提取到产品信息
    $content = str_replace("var bps=","",$content);
    $lists = json_decode($content,true);
    foreach($lists['bankProductList'] as $val) {
        // 在列表页中通过XPath提取到内容页URL
        $content_url = "http://bank.jrj.com.cn/bankpro/product/{$val['inner_Code']}/";
        // 拼出包含产品信息的HTML代码
        $prd_list_info = '<div><a class="sp_prd_list_info">' . json_encode($val).'</a></div>';

        $options = [
            'method'       => 'get',
            'context_data' => $prd_list_info,
        ];

        $phpspider->add_url($content_url, $options);
    }
    // 返回true继续提取其他列表页URL
    return false;
};
//获取到内容页后
$spider->on_content_page = function($page, $content, $phpspider)
{
    return false;
};

//提取到一个field后
$spider->on_extract_field = function($fieldname, $data, $page)
{
    if($fieldname === "sp_prd_list_info"){
        $lists = json_decode($data,true);
        // var_dump($lists);die;
        $data = $lists;
    }
    if(in_array($fieldname,["安全性评级","综合评级","收益性评级","流动性评级"])){
        if(preg_match("/(?<=title=\").*?(?=\")/",$data,$tmp)){
            $data = $tmp[0];
        }
    }
    return $data;
};
//提取完所有field后
$spider->on_extract_page = function($page, $fields)
{
    // echo $page['raw'];die;
    // var_dump($page,$fields);die;
    $fields["pro_name"] = $fields['sp_prd_list_info']['prd_Sname'];
    $fields["inner_Code"] = $fields['sp_prd_list_info']['inner_Code'];
    $fields['url'] = $page['url'];
    unset($fields['sp_prd_list_info']);
    return $fields;
};
$spider->start();

```
