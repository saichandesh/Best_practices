# Http clients and Responses

### First and foremost never have different responses for the same status code. 

Eg : If there is a endpoint `v1/search` , it should always send same object structure for all 200 responses and similarly same object for all 400<br/>
Even if the properites are missing in the response, they have to be null.
<br/><br/>
`First response object for 200`
<br/>
{<br/>
  &nbsp; firstname : 'xy',<br/>
  &nbsp; lastname: 'za',<br/>
  &nbsp; middlename : 'bc'<br/>
}
<br/><br/>
`Second response object for 200, when no middlename is found`<br/>
{<br/>
  &nbsp; firstname : 'xy',<br/>
  &nbsp; lastname: 'za',<br/>
  &nbsp; middlename : null <--- Though there is no middlename, we make it as null so downstreams if people except middlenames to be there always
<br/>}<br/><br/>

