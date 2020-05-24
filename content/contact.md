---
title: Contact
date: 2020-05-24T02:48:58.000+00:00
menu:
  main:
    weight: 5

---
<link rel="stylesheet" href="https://themes.gohugo.io//theme/LoveIt/lib/valine/valine.min.css">
<link rel="stylesheet" href="https://codyjames.dev/uploads/CSS.css">

<div id="valine" class="comment v" data-class="v">
<div class="vpanel">
<div class="vwrap">


<form name="contact" method="POST" data-netlify="true">
	<div class="vheader item2">
    <input class="vinput" type="text" name="name" placeholder="Your Name" />  
    <input class="vinput" type="email" name="email" placeholder="E-Mail" />
    </div>
    <div class="vheader item1">
    <select class="vinput vselect" name="reason[]" placeholder="Reason For Contacting">
      <option value="Computer_Repair">Computer Repair</option>
      <option value="Website_Dev">Website Development</option>
      <option value="Coding">Application Development</option>
      <option value="Tech_Consult">General Tech Consultation</option>
      <option value="Networking">Home Network Setup and Repair</option>
      <option value="Other">Other</option>
    </select>
    </div>
    
 <div class="vedit">
    <textarea class="veditor vinput" name="message" placeholder="Message..."></textarea>
  </div>
  <div class="vrow">
  <div class="vcol vcol-30">
  </div>
  	<div class="vcol vcol-70 text-right">
  	<button class="vsubmit vbtn" type="submit">Send</button>
  	</div>
  	</div>
</form>
</div>
</div>
</div>