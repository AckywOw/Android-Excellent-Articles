��Activity��ʹ��Thread���µ��ڴ�й©
---

> * ԭ������ : [Activitys, Threads, & Memory Leaks](http://www.androiddesignpatterns.com/2013/04/activitys-threads-memory-leaks.html)
* ԭ������ : [AlexLockwood](https://google.com/+AlexLockwood)
* [���ĳ��� :  ��������ǰ�� www.devtf.cn](http://www.devtf.cn)
* ���� : [chaossss](https://github.com/chaossss) 
* У����: [yinna317](https://github.com/yinna317)  
* ״̬ :  ���




> ע����ƪ�����漰��Դ������� [GitHub](https://github.com/alexjlockwood/leaky-threads) ��������Ŷ

�� Android �������������������� Activity ������������Э����ʱ���񣬱���ִ�������²��ײ�����ڴ�й©�������ȶ�һ������Ĵ��룬����д��һ���򵥵� Activity��Activity ��������ͻῪ��һ���̣߳���ѭ��ִ�и��߳��е�����

```java

	/** 
	 *  ʾ��������չʾ���� Activity �����øı�ʱ�����øı�ᵼ�����µ� Activity ʵ������
     *  �٣������⣬Activity �� context Ҳ���ڴ�й©��һ���֣���Ϊÿһ���̶߳�����ʼ
     *  ��Ϊ�����ڲ��࣬ʹ��ÿһ���̶߳�����һ���ⲿ Activity ʵ������ʽ���ã�ʹ��
     *  Activity ���ᱻ Java ���������ջ��ƻ��ա�
     */  
	public class MainActivity extends Activity {
	
	  @Override
	  protected void onCreate(Bundle savedInstanceState) {
	    super.onCreate(savedInstanceState);
	    exampleOne();
	  }
	
	  private void exampleOne() {
	    new Thread() {
	      @Override
	      public void run() {
	        while (true) {
	          SystemClock.sleep(1000);
	        }
	      }
	    }.start();
	  }
	}
```

Activity ���÷����ı��ʹ Activity �����٣����½�һ�� Activity�������ܻ���� Android ϵͳ�Ὣ�뱻���ٵ� Activity ��ص�һ������ɾ������������ Activity �������ڴ棬Activity ִ�е��̵߳ȵȡ���Ȼ������ʵ���Ǻܲп�ģ��ո��ᵽ����Щ���������ᱻ���գ��������ڴ�й©���Ӷ�������Ӱ��Ӧ�õ����ܱ��֡�

## Activity �ڴ�й©�ĸ�Դ ##

������������ǰд��һƪ�й� Handler �� �ڲ���Ĳ��ģ����ҽ�����Ҫ����֪ʶ��϶�֪������ Java �У��Ǿ�̬�����ڲ����������ⲿ�����ʽ���ã������û�п��ǹ���һ�㣬��ô�洢�����ûᵼ�� Activity �������������Ǳ��������ջ��ƻ��ա�Activity ��������� View ���Լ��������������Դ�ļ������ã����仰˵���������ڴ�й©������ Activity �У���ô�㽫��ʧ�������ڴ�ռ䡣

�������������� Activity ���øı�ʱ��������أ���Ϊ Activity �����øı��ʾ Android ϵͳ��Ҫ���ٵ�ǰ Activity ���½�һ�� Activity��������˵�ɣ���ʹ��Ӧ�õ�ʱ����ִ����10�κ���/����������ÿһ�η���ĸı䶼��ִ������Ĵ��룬��ô���ǻᷢ�֣�ʹ��[ Eclipse ���ڴ��������](http://www.eclipse.org/mat/)���Կ�����ÿһ�� Activity ���󶼻���Ϊ����һ����ʽ���ö����������ڴ��С�

![](http://www.androiddesignpatterns.com/assets/images/posts/2013/04/15/activity-leak.png)

ÿһ�����õĸı䶼��ʹ Android ϵͳ�½�һ�� Activity ���Ѹı�ǰ�� Activity �����������ջ��ƻ��ա�����Ϊ�̳߳��о� Activity ����ʽ���ã�ʹ�� Activity û�б��������ջ��ƻ��ա�����������ᵼ��ÿһ���½��� Activity ���������ڴ�й©���� Activity ��ص�������Դ�ļ�Ҳ���ᱻ���գ����е��ڴ�й©�ж����ؿ����֪��

��������������ܺ��£��ܻ֣̿��������������Ǹ���ô�졭��Ī�ţ�����취�ǳ��򵥣���Ȼ�����Ѿ�ȷ��������ĸ�Դ����ô��֢��ҩ�Ϳ����ˣ����ǰѸ��߳�������Ϊ˽�еľ�̬�ڲ���Ϳ��Խ��������⣺

```java

	 /**
      * ʾ��ͨ�����߳�������Ϊ˽�еľ�̬�ڲ�������� Activity context ���ڴ�й©���⣬��
      * �����÷����ı���߳���Ȼ��ִ�С�ԭ�����ڣ�DVM ������������������̵߳����ã�����
      * ��Щ�߳��Ƿ񱻻��գ����� Activity �����������޹ء������е��߳�ֻ��������У�ֱ��
      * Android ϵͳ������Ӧ�ý���ɱ��
      */ 
	public class MainActivity extends Activity {
	
	  @Override
	  protected void onCreate(Bundle savedInstanceState) {
	    super.onCreate(savedInstanceState);
	    exampleTwo();
	  }
	
	  private void exampleTwo() {
	    new MyThread().start();
	  }
	
	  private static class MyThread extends Thread {
	    @Override
	    public void run() {
	      while (true) {
	        SystemClock.sleep(1000);
	      }
	    }
	  }
	}
```

ͨ������Ĵ��룬���߳���Ҳ�������һ���ⲿ Activity ����ʽ���ã����Ҹ� Activity Ҳ�������øı�󱻻��ա�

## �߳��ڴ�й©�ĸ�Դ ##

�ڶ��������ǣ�����ÿ���½� Activity,��� Activity �е��̷߳��������ڴ�й©����Java���߳����������ջ��Ƶĸ�Դ��Ҳ����˵��������ϵͳ��DVM������ܻ�ʹӲ��������������״̬�Ľ��̵����ã�������´�������״̬���߳̽���Զ���ᱻ���ա���ˣ������Ϊ��ĺ�̨�߳�ʵ�������߼���������һ�ֽ���취��

```java

	/**
     * ����������Ҫʵ�������߼��Ա�֤�̲߳��ᷢ���ڴ�й©�����������ʾ��2��ͬ�����˳���ǰ
     * Activity ǰʹ�� onDestroy() ������������������߳��Ǹ������ѡ��
	 */
	public class MainActivity extends Activity {
	  private MyThread mThread;
	
	  @Override
	  protected void onCreate(Bundle savedInstanceState) {
	    super.onCreate(savedInstanceState);
	    exampleThree();
	  }
	
	  private void exampleThree() {
	    mThread = new MyThread();
	    mThread.start();
	  }
	
      /**
	   * ˽�еľ�̬�ڲ��಻��������ⲿ������ã�ʹ�� Activity ʵ�����������øı�ʱ������
	   * ��й©
       */
	  private static class MyThread extends Thread {
	    private boolean mRunning = false;
	
	    @Override
	    public void run() {
	      mRunning = true;
	      while (mRunning) {
	        SystemClock.sleep(1000);
	      }
	    }
	
	    public void close() {
	      mRunning = false;
	    }
	  }
	
	  @Override
	  protected void onDestroy() {
	    super.onDestroy();
	    mThread.close();
	  }
	}
```

ͨ������Ĵ��룬������ onDestroy() �����н������̣߳�ȷ�����ᷢ��������̵߳��ڴ�й©���⡣�������Ҫ�����øı�������̣߳�������ÿһ���ڹر� Activity ��Ҫ�½�һ���̣߳������ҽ�����ʹ�� Fragment ȥ��ɸú�ʱ��������Է�����ǰ�Ĳ��ģ�һ������**��Handling Configuration Changes with Fragments��**Ӧ�����������������API demo��Ҳ�ṩ�˺ܺ�����������Ϊ�������ظ��

## ���� ##

Android ���������У��� Activity ������������Э����ʱ������ܻ�����ѣ���һ��С�ľͻᵼ���ڴ�й©���⡣������һЩС��ʾ���ܰ�����Ԥ���ڴ�й©����ķ�����

- **������ʹ�þ�̬�ڲ�������ǷǾ�̬�ڲ��ࡣ**ÿһ���Ǿ�̬�ڲ���ʵ���������һ���ⲿ������ã����������� Activity �����ã���ô�� Activity �ڱ�����ʱ���޷������ա������ľ�̬�ڲ�����Ҫһ����� Activity ��������ȷ�������ܹ��������У���ô���ȷ�����ڶ�����ʹ�õ���һ�� Activity �������ã�������� Activity ���ᷢ��������ڴ�й©��

- **��Ҫ������ Java ���������ջ��ƻ�����������ڴ�������⡣**���������ʾ����������Ϊ�������ջ��ƻ�����ǽ�����Ҫʹ�õ��ڴ���գ����磺������Ҫ����һ�� Activity����ô����ʵ������ص��̶߳��ñ����ա�����ʵ�����������Ǿ籾�����ߡ�Java �̻߳�һֱ��ֱ�����Ƕ�����ʽ�رգ��ֻ�������̱� Android ϵͳɱ�������ԣ�Ϊ��ĺ�̨�߳�ʵ�������߼�������ʹ���߳�ʱ����ʱ�����ǵ�ϸ�ڣ����⣬������������߼�ʱҪ���� Activity ����������ȥ��ƣ�������� Bug��

- **�������Ƿ������Ҫʹ���̡߳�**Android Ӧ�õĿ�ܲ�Ϊ�����ṩ�˺ܶ���ڿ�����ִ�к�̨�������ࡣ���磺���ǿ���ʹ�� Loader ������ Activity ���������������߳�ͨ��ע��ִ�ж��ݵ��첽��̨��ѯ������������ Service ���ṹ֪ͨ�� UI �� BroadcastReceiver����󣬼�ס����ƪ�����ж��߳̽��е�����ͬ�������� AsyncTask����Ϊ AsyncTask ʹ�� ExecutorService ִ���������񣩡�Ȼ������˵ ExecutorService ֻ���ڶ��ݲ������ĵ�˵��༸�룩�б�ʹ�ã���ô��Щ�������µ� Activity �ڴ�й©Ӧ����Զ���ᷢ����

��ƪ���ĵ�Դ������� [GitHub](https://github.com/alexjlockwood/leaky-threads) �����أ���Ҳ������ [Google Play](https://play.google.com/store/apps/details?id=com.adp.leaky.threads) ���� APK ʹ�á�

![](http://www.androiddesignpatterns.com/assets/images/posts/2013/04/15/leaky-threads-screenshot.png)