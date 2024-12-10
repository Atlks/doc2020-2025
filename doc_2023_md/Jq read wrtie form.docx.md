Jq read wrtie form




Ui.js

function  loadToForm(data,formname)
{
   $.each(data, function(key, value) {
       $('#'+formname+' [name="' + key + '"]').val(value);
   });


}

