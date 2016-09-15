# Sublime Text 3 安装 Package Control && MarkDown Preview 插件


## 自动安装 Package Control 插件

 使用 `Ctrl+~` 快捷键打开命令行或者通过 `View->Show Console`菜单打开命令行， 粘贴如下代码：
#### Sublime Text 3 自动安装代码
```
    import urllib.request,os,hashlib
    h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'
    pf = 'Package Control.sublime-package'
    ipp = sublime.installed_packages_path()
    urllib.request.install_opener( urllib.request.build_opener( urllib.request.ProxyHandler()) )
    by = urllib.request.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read() 
    dh = hashlib.sha256(by).hexdigest()
    print('Error validating download (got %s instead of %s), please try manual install' % (dh, h)) if dh != h else open(os.path.join( ipp, pf), 'wb' ).write(by)
```
>[代码来源](https://packagecontrol.io/installation)

#### Sbulime Text 2 自动安装代码
```
import urllib2,os,hashlib; 
h = '2915d1851351e5ee549c20394736b442' + '8bc59f460fa1548d1514676163dafc88'; 
pf = 'Package Control.sublime-package'; 
ipp = sublime.installed_packages_path(); os.makedirs( ipp ) if not os.path.exists(ipp) else None; 
urllib2.install_opener( urllib2.build_opener( urllib2.ProxyHandler()) ); 
by = urllib2.urlopen( 'http://packagecontrol.io/' + pf.replace(' ', '%20')).read(); 
dh = hashlib.sha256(by).hexdigest(); open( os.path.join( ipp, pf), 'wb' ).write(by) if dh == h else None; 
print('Error validating download (got %s instead of %s), please try manual install' % (dh, h) if dh != h else 'Please restart Sublime Text to finish installation')
```
>[代码来源](https://packagecontrol.io/installation)
## 自动安装 MarkDown Preview 插件

  使用 `Ctrl+Shift+P` 快捷键打开插件管理工具，输入 `pci` 会有MarkDown Preview 插件的选项，选中，然后按 `Enter` 按键。Sublime Text 3 自动安装这个插件。左下角有一个符号一直在动，说明正在安装中.....

#### 自定义 MarkDown Preview 插件的快捷键

  我们可以自定义在浏览器预览的快捷键，点击 Preferences ->  Key Binding User, 输入：
  `{ "keys": ["alt+m"], "command": "markdown_preview", "args": {"target": "browser", "parser":"markdown"} }`
  保存后， 直接输入快捷键： `Alt + M` 就可以直接在浏览器中直接一栏生成的 `HTML`文件了。
