
项目说明




1. web
{
	html位置
	/www/
}	

2. cgi
{
	源码目录
	/home/peng/work/cgi

	make
	cp ./out/*.cgi /www/cgi-bin/

	bin文件目录
	/www/cgi-bin/	
}
	
3. boa
{
	代码位置
	/home/peng/work/boa/boa-0.94.13/src
	
	配置文件
	/etc/boa/boa.conf
	{
		114 DocumentRoot /www
		126 DirectoryIndex index.html
		196 ScriptAlias /cgi-bin/ /www/cgi-bin/
	}
}


 
4. 主控
{
	源码位置
	/home/peng/work/mainthread
}

5. 摄像头
{
	虚拟机->可移动设备->摄像头
	
	/home/peng/work/camera/mjpg-streamer/mjpg-streamer

	运行脚本
	{
		sudo ./start.sh
		
		配置
		./mjpg_streamer -i "./input_uvc.so -y -d /dev/video0" -o "./output_http.so -w ./www" -o "./output_file.so -f /www/pice -d 150000"  
		{
			jpeg摄像头去掉-y
			摄像头对应字符设备 /dev/video0，如果不一致需要修改
			照片存储目录/www/pice
			自动拍照时间 150000
		}
	}
}

6. 数据库sqlite3
{
	CREATE TABLE IF NOT EXISTS user(name text not null, password text not null);
	INSERT INTO user VALUES('user','admin');
}

7. 消息队列
{
	sudo touch /app
	sudo chmod 644 /app
}