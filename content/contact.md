---
title: "Contact"
date: 2020-05-23T22:48:58-04:00
draft: false
---
<div class="vpanel">
<div class="vwrap">

<form name="contact" method="POST" data-netlify="true">
	<div class="vheader item3">
    <input type="text" name="name" placeholder="Your Name"/>  
  
    <input type="email" name="email" placeholder="E-Mail" />
  
    <select name="reason[]" multiple>
      <option value="Computer_Repair">Computer Repair</option>
      <option value="Website_Dev">Website Development</option>
      <option value="Coding">Application Development</option>
      <option value="Tech_Consult">General Tech Consultation</option>
      <option value="Networking">Home Network Setup & Repair</option>
      <option value="Other">Other</option>
    </select>
    </div>
 <div class="vedit">
    <label>Message: <textarea name="message"></textarea></label>
  </div>
  <div class="vrow">
  	<div class="text-right">
  	<button type="submit">Send</button>
  	</div>
    
  </p>
</form>
</div>
</div>