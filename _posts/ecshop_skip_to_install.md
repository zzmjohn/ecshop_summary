### ECSHOP访问首页一直跳转到安装目录解决方案 

使用ecshop建站的站长们可能知道，在ecshop安装完成后，在后台会有一个提示：请删除install文件夹。这个提示是为了避免重复安装，以及为了程序的安全而设定的。今天无忧主机小编就遇到这样一个问题：客户在成功安装ecshop之后，为了去掉后台“请删除install文件”的提示，把install文件夹还有一个demo的文件夹删除了。之后访问首页就出现一个奇怪的问题：每次都会跳转到install/index.php这个安装引导页面上了。
又由于删除了install文件夹，所以这个页面也就变成了404的提示。
对于这个问题，无忧主机小编最开始的判断是由于缓存引起的
于是先去后台清理了缓存，也清理了浏览器的缓存，但是问题依旧存在。
无忧主机小编又想到了默认首页的问题。但是当小编设置默认首页为index.php之后还是没有效果。那为什么会出现这个问题呢？
经过仔细查看根目录下的index.php，小编发现：该文件中具有判断是否有install.lock文件存在data里、或者存在includes里面。如果没有，就会自动跳转到install的安装向导去。判断代码如下： 

所以解决方案很简单，由于只需要一个install.lock文件，而该文件并不需要添加代码，所以我们在data目录下手动创建一个install.lock文件，问题便得到了解决。