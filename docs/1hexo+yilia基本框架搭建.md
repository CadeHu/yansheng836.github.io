# **hexo+yilia������ܴ**

## һ��Ŀ��

�hexo+yilia�Ļ����Ŀ�ܣ����Ҳ�����github���棬�ܹ�ͨ��github pages ���з��ʡ�

ͳһ˵�����ҵ�hexo��Ŀ¼ΪHexo���ֿ�Ϊ`yansheng836.github.io`��

## ����׼������

������ϸ���ܣ��ɲο�hexo�ٷ��ĵ���<https://hexo.io/zh-cn/docs/>��
### 1. ��װgit��
### 2. ע��github���½�һ������Ĳֿ�(username.github.io)��
### 3. ��װNode.js��


## ������װhexo������ʼ��

�ο������̳̣�<https://hexo.io/zh-cn/index.html>

������Ҫ��װhexo�ĵط���git�����й��ߣ�����һ�����ע��#��ͷΪע�ͣ�

```shell
# ȫ�ְ�װhexo
# ����ʼ��һ���ļ���Hexo��Ϊhexo�ĸ�Ŀ¼�����Զ��壬�����ʽΪ`hexo init <folder>`��
# ����Hexo�ļ���
# npm install��Hexo ������ָ���ļ������½�����Ҫ���ļ���
# hexo server�������ڱ��أ������ѿ�ͨ��`http://localhost:4000`���ʣ�`Ctrl+C`��ֹͣ

npm install hexo-cli -g	
hexo init Hexo
cd Hexo
npm install
hexo server
```

![eZEIaj.jpg](https://s2.ax1x.com/2019/07/25/eZEIaj.jpg)



## �ġ���������

### 4.1 �������
Ĭ��������`landscape`�������Ǻܺÿ���һ�㶼��������⡣

���ڱȽ����е������漸�֣�������ʽ��github���涼�У�������Ҳ����ȥ�����ʡ���
 - next: Elegant theme for Hexo.<https://github.com/iissnan/hexo-theme-next>����ֹͣ���£����ߣ��µģ�
<https://github.com/theme-next/hexo-theme-next>

   ![eZE5ZQ.jpg](https://s2.ax1x.com/2019/07/25/eZE5ZQ.jpg)

 - yilia:һ��������ŵ�hexo���� A simple and elegant theme for hexo. <https://github.com/litten/hexo-theme-yilia>

![eZEhqg.jpg](https://s2.ax1x.com/2019/07/25/eZEhqg.jpg)



### 4.2 ����yilia����ļ򵥽���

��ѡ����yilia�������ǰ�װ��ʽ���ο���
- yilia �Ĳֿ���ܣ�����˵������<https://github.com/litten/hexo-theme-yilia>��
- yilia �Ĳֿ������ `litten` �Ĳ��ͱ��ݲֿ⣺<https://github.com/litten/BlogBackup>��

�������Ĳ��Ǹ����⣬�����ο�����
ע�⣺һ��Ĭ�϶����ڲ��͸�Ŀ¼��git�����У�������Щ���롣


#### ��װ
```
$ git clone https://github.com/litten/hexo-theme-yilia.git themes/yilia
```

#### ����

�޸�hexo��Ŀ¼�µ� `_config.yml` �� `theme: yilia`

<font color="red">ע�⣺��ǿ�ƣ����������ʽ������ʱ��ð�ź���Ҫ��Ӣ�Ŀո񣻣��Ƽ�������ļ������������ע�ͣ�ͳһ���ļ���ʽΪUTF-8</font>��


#### ����
����������Ѿ��ܾ�û�и����ˣ������һ�θ��º�����2017��ġ�
```
cd themes/yilia
git pull
```

#### ����

```
hexo clean
hexo generate
hexo server
```
��������ʣ�<http://localhost:4000/>��ע������ڼ䲻�ܰ�ֹͣ����`Ctrl+C`,��Ȼ��ֹͣ����ҳ��404��


Ч��ͼ��

![eZEoIs.jpg](https://s2.ax1x.com/2019/07/25/eZEoIs.jpg)

   

##  �塢��hexo����github���棬ʵ��˫��֧����

����master��֧��`README.md`�е��й�˫��֧�Ĳ���˵����
```
yansheng836.github.io
-- master  �����֧����Ҫ������ɵľ�̬�ļ������ڲ���github pages
-- blog    д����֧����Ҫ���hexo�������á����ͣ�md��
```

### 1. ����master��֧

#### 1.1 ָ��hexo����ķ�ʽ���ֿ⡢��֧
�޸�hexo��Ŀ¼�µ� `_config.yml`
```yml
#����github�Ĳֿ�
#Deployment
#Docs: https://hexo.io/docs/deployment.html
deploy:
  type: git
  repository: https://github.com/yansheng836/yansheng836.github.io.git
  branch: master
```

#### 1.2  Ϊ��Ŀ���˵��README.md
����԰�`README.md`,`LICENSE`�����֤�����ļ�����/source/Ŀ¼�£���Ŀ¼���ļ������ϴ���github��Ŀ¼��֮ǰ���`hexo g`�ǽ�/source/*/*.md�����ļ���Ⱦ��html�ļ������û������������Ⱦ�Ļ�����Ȼ��ŵ���Ӧ��/public/Ŀ¼�£������������ļ���ֱ�Ӹ��Ƶ���Ӧ�ļ����¡�

����������ȾREADME.md����Ҫ�޸�hexo��Ŀ¼�µ� `_config.yml`
```yml
#hexo g ��Ĭ�Ͻ�����md�ļ�ת���ɣ���Ⱦ�ɣ�HTML�ļ��ŵ�public�ļ����У�������仰����˼���Ǹ���hexo�Ľ�������������Ⱦ(skip_render)README.md�ļ�
skip_render: 
 - 'README.md'
```
��������ø����ԣ�README.md�ļ��ᱻװ����README.html�ļ���ͬ�������ͨ��������������Ⱦ�㲻ϣ��hexo��Ⱦ��md�ļ���


#### 1.3 ��master��֧����github��master��֧
������޸������ļ�����ö��������±��롣

```
hexo clean
hexo g
hexo d
```

����������ƴ���
```
ERROR Deployer not found: git
```
��Ҫ���git������
```
npm install hexo-deployer-git --save
```

### 2. ����blog��֧

ע�⣺�÷�֧�����Զ��塣

#### 2.1 ��Hexo��Ŀ¼��git�����У���ʼ��һ���ֿ�

��hexo��Ŀ¼���½��ֿ⣬���ڹ���д����֧��֮ǰ�Ĳ���github��Ϊ�����֧��
```
git init
git remote add origin https://github.com/yansheng836/yansheng836.github.io.git
```


#### 2.2 ����һЩ����Ҫ���ݵ��ļ�

�޸ĸ�Ŀ¼�µ�`.gitignore`��.gitignore��ԭ���ݣ�
```gitignore
.DS_Store
Thumbs.db
db.json
*.log
node_modules/
public/
.deploy*/
```

�ں��������������ݣ���������ԭ���������ļ���
```
#ignored the useless themes
/themes/landscape/
```

#### 2.3 ɾ��`/themes/yilia/.git`�ļ��С�

Ϊ���㽫yilia���������ý���ͬ������ʵ�������Ѿ��ܾ�û�����ˡ�����������֮ǰ����ʹ��github��¡��yilia��Ҳ���ǻ�˵��/themes/yilia/����Ҳ��һ���ֿ⣬���漰��git�ֿ��µ��Ӳֿ�����⣬Ĭ��������ǲ������Ӳֿ���뵽���ֿ�ģ�����������Ҫ����yilia����������ļ���������Ҫɾ�����Ӳֿ⣬��ɾ��`/themes/yilia/.git`�ļ��С�


#### 2.4 ����blog��֧��

����һ����֧���д�����ݣ�����ͬ����ͬһ�ֿ�Ĳ�ͬ��֧�����ύһ�Σ���Ȼ�ᱨ

```
fatal: Not a valid object name: 'master'
```

��ӡ��ύ
```
git add .
git commit -m "init the blog"
```

������֧����ͬ����github��blog��֧
```
git branch blog
git checkout blog
git push origin blog
```

#### 2.5 github�ϰ�blog��֧����ΪĬ�Ϸ�֧

�����ø÷�֧ΪĬ�Ϸ�֧`Settings-->branches-->Default branch:master����Ϊblog-->update`�������Ժ�ֿ���ҳ��ʾ����blog��֧��������ȡ�����߿�¡����ʱ����ȡ�ľ���blog��֧��������ԭ��Ĭ�ϵ�master��֧��


#### 2.6 ʵ��˫��֧����
ÿ��д�격��Ҫͬʱͬ�����òֿ�Ĳ�ͬ��֧�ϣ���ʵ��������ͬ��(����)��
```shell
#Writing
# ͬ����master��֧
hexo clean
hexo generate
hexo deploy

# �ֶ�ͬ����blog��֧��
git add. 
git commit -m "�ύ��Ϣ"
git push origin blog #���������blogΪĬ�Ϸ�֧������ֱ��git push
```


### �塢������github pages

����master��֧Ϊ��ҳ������`Settings-->options-->GitHub Pages:����master��֧-->update`���ɹ����ˢ�£���ʾ���ͨ��`<https://yansheng836.github.io/>`���ʡ�

����й��������������ö�Ӧ������֮ǰҪ����������������������еㆪ�²�ϸ����������ֱ����hexo��Ŀ¼��/source/�ļ��������`CNAME`�ļ�(ע�⣺���ļ�û�к�׺)������Ϊ������
```
www.yansheng.xyz
```
Ȼ�󷢲���github��
```shell
hexo clean
hexo generate
hexo deploy
```

�ɹ�����setting�л���ʾ��ͨ���������ʣ�������ԭ����·����
