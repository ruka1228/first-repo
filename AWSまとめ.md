#授業で使ったサービス
- EC2
- S3
- BeansTalk
- CloudFont
- RDS
- Route53
- ELB
- VPC
- vagrant


[TOC]



##EC2インスタンス立ち上げ手順
- ==EC2==
- S3
- BeansTalk
- CloudFont
- RDS
- Route53
- ELB
- VPC
- vagrant 

１、まずAWSManagement　ConsoleでEC2を選択し、Launch　Instanceをクリック。

２、で使いたいOSを選択。今回はAmazon Linux AMI 2014.09.1 (HVM)を選択。

３、インスタンスのスペックを選択しNext。ここで間違えると処理やスペックはめっちゃ良くなるけどその分のお金がかかるので注意！笑


**４、インスタンスの設定**

![Screenshot from 2014-11-12 10:50:37.png](https://s3-ap-northeast-1.amazonaws.com/i13001/images/Screenshot+from+2014-11-12+10%3A50%3A37.png)
・Number of instancesで立ち上げたいインスタンスの数を選択、
・Auto-assign Public IPでIPを公開
・Shutdown behaviorでTerminateを選択
・でNext


**５、ストレージの選択**

![Screenshot from 2014-11-12 11:01:38.png](https://s3-ap-northeast-1.amazonaws.com/i13001/images/Screenshot+from+2014-11-12+11%3A01%3A38.png)
・使いたい量のストレージの選択、大体デフォルトで大丈夫。
・でNext


**６、インスタンスのTagづけ**

![Screenshot from 2014-11-12 11:10:36.png](https://s3-ap-northeast-1.amazonaws.com/i13001/images/Screenshot+from+2014-11-12+11%3A10%3A36.png)
・画像の記載みたいに分かりやすく自分が分かりやすいようにする
・でNext


**７、Security Groupの設定**

![Screenshot from 2014-11-12 11:17:18.png](https://s3-ap-northeast-1.amazonaws.com/i13001/images/Screenshot+from+2014-11-12+11%3A12%3A38.png)

・ここでSecurity Groupの設定を行う
・でNext

**８、最後にいままで行なった設定の確認**
・最後にKeyの設定

![Screenshot from 2014-11-12 11:17:18.png](https://s3-ap-northeast-1.amazonaws.com/i13001/images/Screenshot+from+2014-11-12+11%3A17%3A18.png)
・あらかじめ作って置いたKeyを選択する。（無かったらつくる）
・でしたのチェックボックスを選択し、Launch Instancesをクリックしインスタンスが立ち上がる。
</br>
</br>


* * *



##S3でWebのアップロード
- EC2
- ==S3==
- BeansTalk
- CloudFont
- RDS
- Route53
- ELB
- VPC
- vagrant 

**１、Create　Bucket**
![Screenshot from 2014-11-12 11:52:00.png](https://s3-ap-northeast-1.amazonaws.com/i13001/images/Screenshot+from+2014-11-12+11%3A52%3A00.png)　　
・Create　BucketでBucket NameとRegionを選択
・Actionsでファイルのアップロードする（HTMｌファイルとか）　　

**２、HTMLを公開する**
　　・アップロードしたHTMLファイルを選択して、ActionsでMake　Publicで公開  

**３、サイトにアクセス**
　　・HTMLファイルを選択し、上のPropertiesでLinkが貼ってあるのでそこにアクセスしたらWebサイトが表示される


## BeansTalkを使う

- EC2
- S3
- ==BeansTalk==
- Clind font
- RDS
- Route53
- ELB
- VPC
- vagrant 


[TOC]



**1,BeansTalkの設定**

　　・最初はGet　Srartedを押す
　　・これでPHPが動くWebサーバーや、ロードバランサー、オートスケールの環境が構築されます。

**２、アプリと環境の設定**

http://www.slideshare.net/shimy_net/aws-elastic-beanstalk-23314834
**AWS Elastic Beanstalk（初心者向け 超速マスター編）JAWSUG大阪**

正直、このサイト（スライド）をみたらおれよりも、上手く説明されている。

**３、これでURLにアクセスしたらサンプルアプリが起動する**



## CloudFontを使ってWebサイトを爆足にする

- EC2
- S3
- BeansTalk
- ==Clind font==
- RDS
- Route53
- ELB
- VPC
- vagrant 
 
 
**１、Webサイトの選択**
　　・Create　DistributionでWebを選択

**２、Origin　Settings**
　　・Origin　Domain NameでURLを選択
　　・Origin　IDを設定
　　・Create　Distributionクリック
  
**３、でWebサイトが爆足になる**

##RDSを使う

- EC2
- S3
- BeansTalk
- Clind font
- ==RDS==
- Route53
- ELB
- VPC
- vagrant 

**１、インスタンスを立ち上げる**
　　・Launch　DB　Insutanceを押して
  　・MY SQLを選択（今回は、）
   ・プランの選択（だいだいはNOで）
   ・スペックを選択（Multi-AZ DeploymentはNOでデータを保管する場所を分布する）
   ・DBの名前とかパスワードを決める
   ・Launch DB　Instanceで完了！






##Route53でEC2インスタンスに固定のIPアドレスを振り分ける

- EC2
- S3
- BeansTalk
- Clind font
- RDS
- ==Route53==
- ELB
- VPC
- vagrant 


[TOC]



**１、あらかじめEC2インスタンスを作って置く**

**２、Route53のHosted Zonesをクリック、（無かったら作る）**
　・aws.cloneko.com.をクリックして、上の「Go to Record Sets」をクリック
　・Create　Record　Setで作る
 
 ![Screenshot from 2014-11-13 10:42:32.png](https://s3-ap-northeast-1.amazonaws.com/i13001/images/Screenshot+from+2014-11-13+10%3A42%3A32.png)

・振り分けたいドメインを記入して
・TypeはIPｖ４にする
・Valueを54.65.64.242にする（立ち上げたインスタンスのIPアドレス）

・Cereateで作れる。


##Route53でS3に固定のIPアドレスを振り分ける

**１、あらかじめS3を作って置く**

**２、Route53のHosted Zonesをクリック、（無かったら作る）**
　・aws.cloneko.com.をクリックして、上の「Go to Record Sets」をクリック
　・Create　Record　Setで作る

**３、S3のファイルの左の虫メガネをクリックしてPropertiesの設定**
　・Static Website Hostingの設定
　　・Enable website hostingを記入項目を２つともindex.htmlにする
　　・Redirect all requests to another host nameを「Redirect all requests to another host name」にする。

**４、Route５３の設定**


![Screenshot from 2014-11-13 10:58:38.png](https://s3-ap-northeast-1.amazonaws.com/i13001/images/Screenshot+from+2014-11-13+10%3A58%3A38.png)

**⇧⇧設定を右側みたいに設定する⇧⇧**

**５、割り当てたドメインにアクセスする**

URL：i13001.aws.cloneko.com.s3-website-ap-northeast-1.amazonaws.com

出来たらOK（少々時間がかかる場合があるが、ちゃんと出来る。）



## VPCインスタンス２つ立ち上げ、一つは、グローバルIPを割り振って、一つはプライベートにする。


- EC2
- S3
- BeansTalk
- Clind font
- RDS
- Route53
- ELB
- ==VPC==
- vagrant 


[TOC]  


**こんなイメージ⇩⇩**

![DSC_0075.JPG](https://s3-ap-northeast-1.amazonaws.com/i13001/images/DSC_0075.JPG)

VPC
でインスタンス２つ立ち上げ、一つは、グローバルIPを割り振って、一つはプライベートにする。



**１、VPCを立ち上げる、**

Create VPCdで、Name tag,CIDR block、Tenancyを設定する
Name tag,　ーーーーi13001
CIDR block、ーーー10.0.0.0/24
TenancyーーーーーDefault

yes,Create




**2、Create subnetをする**

Name,VPC,Availability Zone	,CIDR blockを設定する

Name-ーーーーーーーーーi13001
VPC-ーーーーーーーーーー１で作ったVPCにする
Availability Zoneーーなんでもいい
CIDR blocーーーーーーー１で作ったCIDRにする

yes,Create




**３、EC２でインスタンスを２つ立ち上げ**

１つ目は、普通に立ち上げ、３ページめのnetwork,subnetをさっき作った、VPCとSubnetに設定する。

２つ目は、普通に立ち上げ、３ページ目のnetwork,subnetをさっき作った、VPCとSubnetに設定し、Auto-assign Public IPをEnableに設定する




**4、Route Tablenを作る**

CreateでnametとVPCを設定する



**５、Internet Gatewayを作る**

CreateでNameを入れて作る

Stateが赤になっているのでAttach to VPCで緑にする。


**６、Subnetの設定**

Route tableでeditでCurrent Route TableをおしてRoute Table10.0.0.0/24しか無いものを0.0.0.0/0で一個増やす。


**７、アクセス**
先生のPCに入ってi13001.penをpublicインスタンスに送って入る、そこから、また鍵を今度はプライベートインスタンスに送って入る


## vagrantを使ってEC2インスタンスを５つ立ち上げる

- EC2
- S3
- BeansTalk
- Clind font
- RDS
- Route53
- ELB
- ==VPC==
- vagrant 


[TOC]

**１、vagrant-awsプラグインをインストール**

$ vagrant plugin install vagrant-aws

これでVagrantのプラグインがインストールされる

** ２、Vagrantfileの編集**

　　$　vagrant init

　・Vagrantfile

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
    config.vm.box = "dummy"  # 追加したdummy boxを使用
(1..5).each do |num|
config.vm.define "test#{num}" do |node|
node.vm.provider :aws do |aws, override|
aws.access_key_id = "AKIAIQMVY22QFGKYTJ2Q" **#手順3.2.で作ったAccess Key ID**
aws.secret_access_key = "MN3LbsupUCsbbRNZoYDDrVJDvwRrgxxhTV2Vkfl0"  **#手順3.2.で作ったSecret Access Key**
aws.keypair_name = "i13001"  **#手順3.4.で作ったKey Pair Name**
aws.region = "ap-northeast-1"   **#Tokyoリージョン**
aws.ami = "ami-61477960"        **#AMIのID**
aws.instance_type = "t2.micro"
aws.security_groups = ["i13001"]  **#手順3.5.で作ったSecirity Group Name**
aws.tags = {"Name" => "test#{num}"} **#任意のタグ名**
override.ssh.username = "ec2-user"  **#SSHでログインする際のユーザー名**
override.ssh.private_key_path = "~/.ssh/i13001.pem"
**手順3.5.のKey Pair作成時にダウンロードした秘密鍵ファイルのパス**
end
end
end
end


**３、EC2インスタンスを作る**

$ vagrant up --provider=aws

　・これでEC2インスタンスが５個たち上がる
 
 **４、立ち上げたインスタンスの削除**
 
 　$ vagrant destroy
  
  ・これで立ち上げたインスタンスを簡単に削除出来る。



## VPCにEC2とRDSを入れてwordpressを動かす

- ==EC2==
- S3
- BeansTalk
- Clind font
- ==RDS==
- Route53
- ELB
- ==VPC==
- vagrant 


[TOC]



**こんなイメージ⇩⇩**

![DSC_0077.JPG](https://s3-ap-northeast-1.amazonaws.com/i13001/images/DSC_0077.JPG)

**１、VPCを立ち上げる**
　設定
　　・Subnetは２つ作る
 
 **２、EC2インスタンスを立ち上げる**
 　設定
 　　・グローバルIP選択
   　　・作ったVPCを選択

**３、RDS立ち上げ**
設定
　・VPCは最初はdefaultで
 
**４、作ったRDSの設定**

・左項目のSubnet Groupを選択
・Create DB Subnet Groupで作る
・んで名前とか入れる
・VPC　IDを最初に作ったVPCにする
・下のadd all the subnetをクリックしてSubnetを２つ選択
・でYes、Create

**５、EC2にwordpressが出来る環境設定**
・ApacheとPHPを入れる。
・wgetでwordpressをダウンロード
・ダウンロードしたWordPressを/var/www/htmlに入れる
・ブラウザでアクセス
・で最初の画面が出てくる
・DBをRDSで作ったIPにする














