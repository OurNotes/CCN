总操作流程：
- 1、输入命令
- 2、安装插件

***

# 输入命令

按Ctrl+～打开控制行,输入命令：

```

import urllib.request,os,sys; exec("if sys.version_info < (3,) or os.name != 'nt': raise OSError('This code is for Windows ST3 only!')"); pr='Preferences.sublime-settings'; ip='ignored_packages'; n='Package Control'; s=sublime.load_settings(pr); ig=s.get(ip); ig.append(n); s.set(ip,ig); sublime.save_settings('Preferences.sublime-settings'); pf=n+'.sublime-package'; urllib.request.install_opener(urllib.request.build_opener(urllib.request.ProxyHandler())); by=urllib.request.urlopen('https://packagecontrol.io/'+pf.replace(' ','%20')).read(); open(os.path.join(sublime.installed_packages_path(),pf),'wb').write(by); ig.remove(n); s.set(ip,ig); sublime.save_settings(pr); print('Package Control: 3.0.0 upgrade successful!')

```

# 安装插件

`

ConvertToUTF8

`