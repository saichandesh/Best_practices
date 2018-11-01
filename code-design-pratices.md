# Singleton Vs Static class

As both singleton and Static classes serve the purpose of having one instance or copy of a class over the whole app. Debating here on which wins over the other.
<br/><br/> Battle begins....

### Usage of Static classes
```
# log.ts

import * as Airbrake from 'airbrake';

export default class Logger{

  public static notifier = null;
  
  public static configure(){
    
    Logger.notifier = new Airbrake({ key: '',secret:''});
    
  }
  
}
```
```
# usage-log.ts

import Logger from 'log.ts';

class UsageLogger{
  
  constructor(logger=Logger){}
  
  notify(){
    this.logger.notifier.notfiy('Test');
  }
}
```

As seen above, when unit testing the `UsageLogger` it's easy to mock `Logger` as we can pass `mockLogger` during `Logger` instance creation.<br/>
But to test `Logger` it's hard to mock `Airbrake`. The way we end up will be mock patching.<br/>
If we think we don't need to use unit test, we can go ahead with `static class`, if not go with `Singleton`

### Usage of Static classes
```
# log.ts

import * as Airbrake from 'airbrake';

export default class Logger{

  constructor(airbrake=Airbrake){
    this.notifier = new Airbrake({ key: '',secret:''});
  }
  
}
```
```
# usage-log.ts

import Logger from 'log.ts';

class UsageLogger{
  
  constructor(logger= new Logger()){}  # If we had DI (dependency injection framework, it'll take of it)
  
  notify(){
    this.logger.notifier.notfiy('Test');
  }
}
```
In this case it's easy to mock `Airbrake` in `Logger`
