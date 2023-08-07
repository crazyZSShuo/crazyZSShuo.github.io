## 第一种方式
- 1、访问https://hexed.it/
- 2、点击左上角的打开文件，选择/opt/sublime_text/sublime_text
- 3、 按 `CTRL + F` 或左侧面板中的搜索栏并查找：80 78 05 00 0f 94 C1
- 4、现在在编辑器中，单击第一个字节 (80) 并开始将每个字节替换为：C6 40 05 01 48 85 C9
- 5、最后，再次在左上角单击“导出”按钮。这会将文件下载到您的下载文件夹中。
- 6、执行 sudo cp ~/Downloads/sublime_text /opt/sublime_text/sublime_text 替换原文件。


## 第二种方式
- 1、选择二进制工具打开sublime text可执行文件
- 2、通过单击 Ctrl F 搜索：41 57 41 56 56 57 55 53 B8 28 21 00 00 并将其替换为：33 C0 FE C0 C3 57 55 53 B8 28 21 00 00（RSA 密钥补丁）
- 3、搜索：6C6963656E73652E7375626C696D6568712E636F6D 并将其替换为：7375626C696D6568712E6C6F63616C686F73740000 （禁用许可证检查）
- 4、导出修改后的文件并将其另存为桌面上的 sublime_text.exe 重命名原始文件
- 5、打开新导出文件，然后单击“输入许可证”
- 6、```—– BEGIN LICENSE —– Zer0Daylab Unlimited User License EA7E-81044230 0C0CD4A8 CAA317D9 CCABD1AC 434C984C 7E4A0B13 77893C3E DD0A5BA1 B2EB721C 4BAAB4C4 9B96437D 14EB743E 7DB55D9C 7CA26EE2 67C3B4EC 29B2C65A 88D90C59 CB6CCBA5 7DE6177B C02C2826 8C9A21B0 6AB1A5B6 20B09EA2 01C979BD 29670B19 92DC6D90 6E365849 4AB84739 5B4C3EA1 048CC1D0 9748ED54 CAC9D585 90CAD815 —— END LICENSE ——```
- 7、完成！
