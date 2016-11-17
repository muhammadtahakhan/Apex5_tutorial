             **Apex 5 dynamic menu**
             =======================
**links for study**
https://community.oracle.com/thread/3758579
http://davidsgale.com/apex-5-0-how-to-dynamic-menus-universal-theme/
http://www.talkapex.com/2015/04/apex-5-creating-sub-menus.html
http://vincentdeelen.blogspot.com/2013/10/dynamic-navigation-lists.html

**Description:**
In Apex 5 query for menu should have the following columns "level","label" , "target", "is_current", "image"
OR
"level_value", "label_value", "target_value", "is_current", "image_value"(OR 'fa-book' icon, )
The icon value is font awesome class apex5 has default included font awesome 

Query can be like this:
select   1            as level_value 
       , replace(initcap("PAGE_ALIAS"),'_',' ')  as label_value 
       , 'f?p=&app_id.:'||lower(PAGE_ALIAS) as target_value
       , null         as is_current 
       , null         as image_value 
       , null         as image_attr_value 
       , null         as image_alt_value 
from   apex_application_pages
where  application_id = :APP_ID
and    page_alias is not null 
  and  page_alias not in ('LOGIN_DESKTOP')
order by page_id desc

