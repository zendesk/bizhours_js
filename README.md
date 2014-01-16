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

<p>
<b>constructor</b>
<code>new BizHours(hoursObject)</code>
<br/>
Creates a new BizHours object from hoursObject input.  hoursObject is a javascript obj with keys of ["mon", "tue", "wed", "thu", "fri", "sat", "sun"], and values
of the following format: "9am-1pm, 1:30pm - 5:30pm".
    var h = new BizHours({mon: "9am - 1pm", tue: "11am - 3pm"})
<p>
<b>addDay</b>
<code>.addDay(dayName, timeString)</code>
<br/>
Sets dayName's open hours to the parsed value of timeString.  The format of dayName and timeString follow the constructor's arguments.

    h.addDay("mon", "5pm-7pm")

<p>
<b>merge</b>
<code>.merge(hoursObject)</code>
<br/>
Merge hoursObject (a bizHours object) into this object.
    h.merge(other)
<p>
<b>humanize</b>
<code>.humanize()</code>
<br/>
Return an array objects representing open hours

    > h.humanize()
    [
      {day: "Monday", 
       hours: "9am-5pm"},
      {day: "Tuesday", 
       hours: "9am-5pm"},
      ...
    ]

<p>
<b>humanizeCondensed</b>
<code>.humanizeCondensed()</code>
<br/>
The same as .humanize, but with runs of days that have the same hours collapsed into one array entry:

    > h.humanizeCondensed()
    [
      {day: "Monday - Tuesday", 
       hours: "9am-5pm"},
      {day: "Wednesday", 
       hours: "11am-5pm"},
      ...
    ]




