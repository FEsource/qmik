
Qmik��һ�����ٺ;����JavaScript�⣬����HTML�ĵ����¼������Լ�Ajax������ 
Qmik.sun �Ͱ������ģ��,����ʵ�ְ���Ҫ������Ӧ��js,css�ļ�
Qmik���﷨��jquery��һ�µ�,���Ŀ��С16-23k����,֧��uc,ie>=10,����webkit�ں˵������(��chrom,safari��),firefox; 
	�Ƽ����ƶ�web����.
	
API���:<br/><br/>



			encode(value) :��ͬ��encodeURIComponent
			decode(value) :decodeURIComponent ,
			isBool(value) : �����ж�,
			isString(value) : �ַ����ж�,
			isFun(value) : �����ж�,
			isFunction(value) : �����ж�,
			isNum(value) :�����ж� ,
			isNumber : �����ж�,
			isArray(value) : �����ж�,
			isNull(value) : ��ָ���ж�,
			likeArray(value) : ������,��length�ֶε�һЩ����,
			each(value,function(i,val){}) : ѭ��,
			stringify(value) : jsonת�ַ���,
			parseJSON(value) : �ַ���תjson,
			likeArray(value) : ������
			isDate(value) :,
			isObject(value) : ,
			isPlainObject(value) : 
			likeNull(value) : ���ֵ,�� "","null","undefined",null�Ȼᱻ��ΪTrue,
			inherit(subClass, superClass) : �̳��� ����subClass�̳и���superClass�����Է���, ע:�����и�������Լ�����ʱ,���ᱻ�����滻,
			trim(value) :,
			toLower(value) :�ַ���Сд,
			toUpper(value) : ��д,
			
			merge(arr1,arr2) : merge,	// �ϲ���������
			array(array) : //�ϲ���һ��������,
			inArray(value, array) : �������������λ,
			unique(array) : ����ȥ��,
			contains(grandfather, child) : �����ڵ�,
			map(array, callback) : //�������������,ȫ����һ������ӳ��ת��,
			getScript(url, success, error) :  ȡ�ýű�
			getCss(url, success, error) :  ȡ��css
			serialize(array) : ���������л��� a=b&c=k ���͵��ַ���
			serializeArray(array) : ������ת����[{name:value},{name:value}]�������͵�����,���ԭ������û��name,�������˽ڵ�
			grep(array,callback):����

			param :  ��ȡ��������ÿ��Ԫ�ص�name��value����,ת����һ��url��ʽ(a=b&name=g)���ַ���,����encode
			now([date]) :   ��ǰʱ��
			delay(fun, time, target)  �ӳ�ִ��,����setTimeout,����һ������,�����и� stop����,����ִֹͣ��
			// 
			/**
			 * fun:ִ�еķ���
			 * cycleTime:ִ�е�����ʱ��
			 * ttl:����ʱ��,ִ��ʱ��>ttlʱ,ִֹͣ��,��λ ms(����)
			 * target:apply,call��ָ�����
			 */
			cycle(fun, cycleTime, ttl) :  ����ִ��,������setInterval,�᷵��һ������,�����и� stop����,����ִֹͣ��

			log(msg, event) : ����־
			isIphone : 
			isAndroid :
			isWP : 
			isIE : 
			isFF : is Firefox
			isWK : is Webkit
			isOpera : 
			config(opts, _config) : 

			url(_url) : �ϲ�url,if ���� _urlΪ��,��
			box(callback)  : �쳣���,�����쳣,�����쳣�����������,��Ҫִ��$.config({box:{enable : true}})
			
			
2.��ѯapi:֧������Ĳ�ѯ��ʽ<br/><br/>



			$("#id")
			$(".class")
			$("ul")
			$("#id .class")
			$("#id > .class")
			$(".class div[flag=aaa]")	
	
	
	
<br/><br/>


3.�����������:<br/><br/>


	a. Config.js �ļ�,д��������:
	
	
	
			(function($, define) {
				
				$.config({
					context : "/qmik/",// ����Qmik���̵Ļ���·��,���û������,Ĭ��= location.protocol + "//" + location.hostname
					debug:true,//debugģʽ
					box:{	
						enable : true,//�����쳣�ռ�
						ttl : 20000,//�ռ�ʱ����
						url : "/errorCollect" //�ռ���ַ
					}
				});
		
				// ����ģ����������·��
				$.sun.config({
					//����ϵͳ,��·�������һ��key����ʾ,����ͨ�����key���ҵ���Ӧ��url
					alias : {
						// qmik���
						"Qmik.nav" : $.url("/assets/plugins/Qmik.nav"),//
						///
						//ҵ��ģ��
						"Home" : "module/home/Home",
					},
					preload : [//Ԥ����,�ڼ�������ģ��ǰ,�����ȼ������涨���ģ��
						"Qmik.nav"
					]
				});
			})(Qmik, Qmik.sun.define);
	
	
	b.��index.htmlҳ������js<br/><br/>
	
	
	
			<!-- ���ؿ�� -->
			<script type="text/javascript" src="/xxxx/Qmik.js"></script>
			<!-- ���������ļ� -->
			<script type="text/javascript" src="/xxxx/Config.js"></script>
  
  
  
  c.ʵ��Homeҵ��ģ�鹦��
  
  
  
  		(function($, define) {
  			function Home(nav){
  				this.nav=nav;
  			}
  			Home.prototype.showHome=function(){
  					var me=this;
  					var main = $("#main_module");
						$.get("module/home/home.html", function(data) {
							main.html(data);//�������
							me.doxxx();
						});
  			}

				define(function(require, exports, module) {
					var nav = require("Nav");//��������ģ��
					exports=new Home(nav);
				});
			})(Qmik, Qmik.sun.define);
			
		
			
	 d.ʹ��ģ��,��index.htmlʹ�� Homeģ�鹦��.  ��index.html��β���������´���:
	 
	 
	 
		 	<script type="text/javascript">
				// �����ʼ�� 
				(function($, define) {
					//����3��ģ���ʼ��
					$.use([
						"Nav", "Home"
					], function(nav, home) {
							nav.doxxx();//��ʾͷ������
							home.showHome();//��ʾ��ҳ
					});
				})(Qmik, Qmik.define);
			</script>
			
			
			
			
			
			
4.����Դ��,�Զ��幹��(����ʱ,ֻ��ѡ��srcĿ¼�µ��ļ��ϲ���һ��Qmik.js,���ܰ���plugins������Ŀ¼)

		1.��װgithub�ͻ���,��Ҫʹ�õ�git-shell  (http://windows.github.com/)
		2.���� nodejs ,��װ ,http://nodejs.org/
		3. ��nodejs��bin���õ�path��,(�Ѿ��Դ���npm)
		4.����Git Shell,��������������Դ���ַ,���d:/download/qmik/
				ִ������:
				     	npm uninstall -g grunt  ж�� 
		        	npm install -g grunt-cli  (�Ѱ�װ����gruntָ����ӵ� path�� C:\Users\xxx\AppData\Roaming\npm)
							npm install grunt-contrib-uglify  ��װuglify 
							npm install  grunt-contrib-cssmin  ��װcssmin
							npm install  grunt-contrib-qunit  ��װcssmin
							npm install  grunt-contrib-concat ��װcssmin
							npm install  grunt-contrib-clean  ��װcssmin
							
			 ��װ��ɺ�,����Ŀ¼,ִ��  grunt����,��ʼ�Զ�����,���������Ĵ������ assets Ŀ¼��
			 				