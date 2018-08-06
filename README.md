
#构建libc偏移数据库

##获取所有已配置的libc版本并提取符号偏移量。它不会下载任何两次，因此您也可以使用它来更新您的数据库：
$ ./get


##您还可以向数据库添加自定义libc。
$ ./add /usr/lib/libc-2.21.so


##查找数据库中具有给定地址的给定名称的所有libc。仅检查最后12位，因为随机化通常适用于页面大小级别。
$ ./find printf 260 puts f30
archive-glibc (id libc6_2.19-10ubuntu2_i386)


##从泄漏的返回地址中找到一个libc到__libc_start_main。
$ ./find __libc_start_main_ret a83
ubuntu-trusty-i386-libc6 (id libc6_2.19-0ubuntu6.6_i386)
archive-eglibc (id libc6_2.19-0ubuntu6_i386)
ubuntu-utopic-i386-libc6 (id libc6_2.19-10ubuntu2.3_i386)
archive-glibc (id libc6_2.19-10ubuntu2_i386)
archive-glibc (id libc6_2.19-15ubuntu2_i386)


##在给定libc ID的情况下转储一些有用的偏移量。您还可以提供自己的名称进行转储。
$ ./dump libc6_2.19-0ubuntu6.6_i386
offset___libc_start_main_ret = 0x19a83
offset_system = 0x00040190
offset_dup2 = 0x000db590
offset_recv = 0x000ed2d0
offset_str_bin_sh = 0x160a24


##检查库中是否已存在库。
$ ./identify /usr/lib/libc.so.6
id local-f706181f06104ef6c7008c066290ea47aa4a82c5
