1. download [PHP Markdown Extra](http://michelf.ca/projects/php-markdown/classic/) from [here](http://littoral.michelf.ca/code/php-markdown/php-markdown-extra-1.2.8.zip). and [HTML to markdown](https://github.com/nickcernis/html-to-markdown) from [here](https://raw.githubusercontent.com/nickcernis/html-to-markdown/master/HTML_To_Markdown.php) 

2. Edit /manage_page.php and add the following after 'require config.php'  

	require KU_ROOTDIR . "lib/markdown.php";
	require KU_ROOTDIR . "lib/HTML_To_Markdown.php";


3. Edit /inc/classes/manage.class.php and modify the following:  

For every occurance of  

	$tc_db->qstr($_POST['thing'])
	
where thing is news faq or message, replace it with  

	$tc_db->qstr(Markdown($_POST['thing']))

and for every occurance of  

	htmlspecialchars($values['thing'])
where thing is news faq or message, replace with  

	htmlspecialchars(new HTML_To_Markdown($values['thing']))


on the same page, change  

	intval($_POST['faq'])  

to 

	$tc_db->qstr(Markdown($_POST['faq'])) 
  
###Thats it!  
there should be 6 Markdown(\*)s and and three HTML_to_Markdown(\*)s in /inc/classes/manage.class.php.

Good luck!
