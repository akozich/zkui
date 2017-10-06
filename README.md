# zkui for MacOS
This is a clone of the original [zkui](https://github.com/echoma/zkui) with the prebuild artifact for MacOS.

## Download
[zkui-0.3.dmg](https://github.com/akozich/zkui/releases/download/0.3-mac/zkui-0.3.dmg)

## Or build yourself
PyQt5 no longer has PyQtWebkit so you'll have to build pyqt5 from sources. Qt5 itself can be installed from Homebrew:

```
brew install qt@5.5

mkdir /tmp/qt
cd /tmp/qt
curl -O https://kent.dl.sourceforge.net/project/pyqt/sip/sip-4.18.1/sip-4.18.1.tar.gz
tar xvf sip-4.18.1.tar.gz
cd sip-4.18.1/
python3 configure.py -d /usr/local/lib/python3.6/site-packages -b /usr/local/bin -e /usr/local/include -v /usr/local/share/sip --arch x86_64
make
make install
cd ..


curl -O https://kent.dl.sourceforge.net/project/pyqt/PyQt5/PyQt-5.5.1/PyQt-gpl-5.5.1.tar.gz
tar xvf PyQt-gpl-5.5.1.tar.gz
cd PyQt-gpl-5.5.1/
python3 configure.py --confirm-license -d /usr/local/lib/python3.6/site-packages -b /usr/local/bin --qmake /usr/local/opt/qt\@5.5/bin/qmake --sip-incdir /usr/local/include -v /usr/local/share/sip/Qt5 --no-qml-plugin --no-designer-plugin
make
make install
```

Then build the project itself as described in the original project 

When the binary is built using `cx_freeze` all installed packages can be removed

```
python3 -m pip uninstall kazoo pyyaml cx_Freeze 
brew uninstall qt@5.5
rm -rf /usr/local/bin/sip /usr/local/include/sip.h /usr/local/include/sip.h /usr/local/lib/python3.6/site-packages/sip*
rm -rf /usr/bin/{pyuic5,pyrcc5,pylupdate5} /usr/local/lib/python3.6/site-packages/PyQt5
```
