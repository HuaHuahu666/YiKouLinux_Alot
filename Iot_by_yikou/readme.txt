
��Ŀ˵��




1. web
{
	htmlλ��
	/www/
}	

2. cgi
{
	Դ��Ŀ¼
	/home/peng/work/cgi

	make
	cp ./out/*.cgi /www/cgi-bin/

	bin�ļ�Ŀ¼
	/www/cgi-bin/	
}
	
3. boa
{
	����λ��
	/home/peng/work/boa/boa-0.94.13/src
	
	�����ļ�
	/etc/boa/boa.conf
	{
		114 DocumentRoot /www
		126 DirectoryIndex index.html
		196 ScriptAlias /cgi-bin/ /www/cgi-bin/
	}
}


 
4. ����
{
	Դ��λ��
	/home/peng/work/mainthread
}

5. ����ͷ
{
	�����->���ƶ��豸->����ͷ
	
	/home/peng/work/camera/mjpg-streamer/mjpg-streamer

	���нű�
	{
		sudo ./start.sh
		
		����
		./mjpg_streamer -i "./input_uvc.so -y -d /dev/video0" -o "./output_http.so -w ./www" -o "./output_file.so -f /www/pice -d 150000"  
		{
			jpeg����ͷȥ��-y
			����ͷ��Ӧ�ַ��豸 /dev/video0�������һ����Ҫ�޸�
			��Ƭ�洢Ŀ¼/www/pice
			�Զ�����ʱ�� 150000
		}
	}
}

6. ���ݿ�sqlite3
{
	CREATE TABLE IF NOT EXISTS user(name text not null, password text not null);
	INSERT INTO user VALUES('user','admin');
}

7. ��Ϣ����
{
	sudo touch /app
	sudo chmod 644 /app
}