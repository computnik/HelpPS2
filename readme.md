
### STATUS: UNSUPPORTED

![No Support/Maintenance Available](https://img.shields.io/badge/SUPPORT-UNSUPPORTED-red)
![Deprecated Status](https://img.shields.io/badge/STATUS-DEPRECATED-red)
![Last Tested in 2016](https://img.shields.io/badge/last%20tested-2016-orange)

## PS2 Form Helper for BITS Pilani


> This is a updated version of Tarang Shah's script (Last tested: 2016). He is the original author and this is an adaption and update to work with current PS2 stations. For original script checkout https://github.com/t27/ps2helper


This a tool which will help you fill the PS2 (Practice School 2) Preferences on the new BITS Pilani PSMS page. You will need to sort the PS stations in Excel(Or any other spreadsheet software which supports csv files) using the **given csv file** which has **Station IDs**,Names, Stipend, Location, Disciplines etc as columns.

*Please keep in mind that Station IDs are 2-4 digit numbers which are given in the csv file given here - [Problem Bank CSV](https://raw.githubusercontent.com/computnik/HelpPS2/master/stations.csv).* 

We recommend using Chrome.

This has been tested to work fine on Chrome in Windows and Ubuntu.


Thanks to Apoorv Umang and @t27 Tarang Shah for contributing.


#### DISCLAIMER:
> By using this script, you are taking full responsibility of the consequences. Use at your own risk.
This script is intended for general use and no warranty is implied for suitability to any given task.
I hold no responsibility for your setup or any damage done while using/installing/modifing this script.
You MUST cross check your preferences manually after using this script to ensure it is correct.  

### Instructions

1. Firstly add the bookmarklet below to your bookmarks bar. (Press CTRL+SHIFT+B to display the bookmarks bar, then right click on it and click on Add Page, Change the title to whatever you want and in the url field, paste all of the below text)


```
javascript:(function(){function r(e,t,n){$.ajax({type:"POST",url:"StudentStationPreference.aspx/saveStudentStationPref",contentType:"application/json; charset=utf-8",data:'{ jsondata: "'+encodeURIComponent(e)+'", jsonvalue: "'+encodeURIComponent(t)+'",  contistation: "'+encodeURIComponent(n)+'"}',dataType:"json",success:function(e){alert("Station Preference Submitted Successfully");window.location.replace("FillProbBankSkills.aspx")}})}function i(){var e=$("#prefOrder2").val();alert(e)}function s(){var e=$("#prefOrder2").val().split("\n");jsondata="[";var t=true;if(e.length!=368){alert("Didnt find Exactly 368 stations!");return}for(var n=0;n<e.length;n++){if(!e[n].match(/^\d+$/)){alert("Found non numeric value in pasted data!");return}jsondata+="{";jsondata+="'isActive':'1',";jsondata+="'PreferenceNo':'"+(n+1)+"','StationId':'"+e[n]+"',";jsondata+="'Accommodation':'"+t+"',";jsondata+="},"}jsondata=jsondata.substr(0,jsondata.length-1);jsondata+="]";var i="";var s=0;r(jsondata,i,s)}function o(){(window.myBookmarklet=function(){var e=document.createElement("input");e.setAttribute("type","button");e.setAttribute("value","Submit");e.setAttribute("class","btn btn-primary");e.setAttribute("id","submitPrefs");var t=document.createElement("textarea");t.setAttribute("rows","2");t.setAttribute("id","prefOrder2");if(document.getElementById("submitPrefs")==null){document.getElementById("btnSave").parentNode.insertBefore(t,null);document.getElementById("btnSave").parentNode.insertBefore(e,null);document.getElementById("submitPrefs").onclick=s}else{alert("You Only Click Once")}})()}var e="1.3.2";if(window.jQuery===undefined||window.jQuery.fn.jquery<e){var t=false;var n=document.createElement("script");n.src="http://ajax.googleapis.com/ajax/libs/jquery/"+e+"/jquery.min.js";n.onload=n.onreadystatechange=function(){if(!t&&(!this.readyState||this.readyState=="loaded"||this.readyState=="complete")){t=true;o()}};document.getElementsByTagName("head")[0].appendChild(n)}else{o()}})();

```


2. Sort the [Problem Bank CSV](https://raw.githubusercontent.com/computnik/HelpPS2/master/stations.csv) according to your preferences in a software of your choice(Excel or otherwise).
3. Login on the PSMS site and go to the preferences page
4. Once the page loads completely, click on the previously created bookmark in your bookmarks bar
5. You should see a text box and a button appear below the Save preferences button.
6. Now copy the Station Id column from your sorted csv list and paste it into the text box. 
    *Ensure that you dont copy the column title, and that your cursor ends on the last number and NOT on a new line*
7. Each Station ID should be on a **new line**(default nature of a copy from excel)
8. Now click on the Submit button, all your acco fields will be ticked for you!
9. You'll get a popup confirming the submission.
10. Now refresh your preferences page and see the result!
