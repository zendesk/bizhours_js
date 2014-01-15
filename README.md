# bizhours.js 

bizhours.js is a lightweight javascript library for parsing storing, displaying and querying
a business' open hours.  It's developed and maintained at Zendesk for the link-sf.org project.

## howto use

     > var h = new BizHours({sun: "9am-7pm", mon: "10am-7pm", wed: "4am-5am", thu: "4am-5am"})
     > h.humanize().forEach(function(day) { 
          console.log(day.day); 
          console.log(day.hours) 
       });

       Sunday
       9am - 7pm
       Monday
       10am - 7pm
       Tuesday
       null
       Wednesday
       4am - 5am
       Thursday
       4am - 5am
       Friday
       null
       Saturday
       null
    
     > h.humanizeCondensed().forEach(function(range) {
          console.log(range.day);
          console.log(range.hours)
       });

       Sunday
       9am - 7pm
       Monday
       10am - 7pm
       Wednesday - Thursday
       4am - 5am

## more:




