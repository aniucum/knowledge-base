- example 1
```bash
filter {
  if ![age] or [age] == "" {
       mutate {
         update => { "age" => "0" }
       }    
   }
}
```
- example 2 (check!)
```bash
if ([mesage] =~ /(RECEIVE|SEND)/) {
   grok {
      // do your grok here
   }
} else if ([message] =~ /RemoteInterpreter/) {
   grok {
      // do some other grok here
   }
}
```
