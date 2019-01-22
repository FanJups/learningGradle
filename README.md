# learningGradle
I am learning Gradle using https://www.tutorialspoint.com/gradle/index.htm
## convert gradle to maven
https://www.google.com/search?q=convert+gradle+to+maven&oq=convert+gradle+&aqs=chrome.1.69i57j0l5.12342j1j7&sourceid=chrome&ie=UTF-8

https://stackoverflow.com/questions/12888490/gradle-build-gradle-to-maven-pom-xml

## could not find method left shift()

https://www.google.com/search?q=could+not+find+method+left+shift()&oq=could+not+find+method&aqs=chrome.5.69i57j0l5.27540j0j7&sourceid=chrome&ie=UTF-8

https://stackoverflow.com/questions/33727502/gradle-leftshift-operator-with-task-needed-is-it-superfluous

## could not find method left shift() for arguments on task

https://www.google.com/search?ei=tI1GXJK3Kc7QaLD2ptAI&q=could+not+find+method+left+shift%28%29+for+arguments+on+task&oq=could+not+find+method+leftshift&gs_l=psy-ab.1.4.0i10l2j0i203l2j0i10i203j0i203j0i10i203j0i22i10i30j0i22i30.623333.686075..699619...29.0..2.128.3601.47j5......0....1j2..gws-wiz.....6..35i39j0i13i10j0i13i10i30j0i13i30j0i67j0i131j0j0i20i263j35i304i39j0i13.JvIbfKOpgBA


## << is deprecated

https://github.com/researchgate/gradle-release/issues/214

## Adding dependecy on a task by using closures 

This following code doesn't work : BUILD FAILED ( could not determine the dependencies of task :taskX ) 

    task taskX << {
     println 'taskX'
    }
     taskX.dependsOn {
     tasks.findAll { 
        task → task.name.startsWith('lib') 
     }
    }
    task lib1 << {
     println 'lib1'
    }
    task lib2 << {
     println 'lib2'
    }
    task notALib << {
     println 'notALib'
    }
    
After searching about errors

### could not determine the dependencies of task :taskX

Nothing to show but after searching about "tasks.findAll { task → task.name.startsWith('lib') }"

#### tasks.findAll { task → task.name.startsWith('lib') }

https://www.google.com/search?q=tasks.findAll+%7B+task+%E2%86%92+task.name.startsWith(%27lib%27)+%7D&oq=tasks.findAll+%7B+task+%E2%86%92+task.name.startsWith(%27lib%27)+%7D&aqs=chrome..69i57.2225j0j7&sourceid=chrome&ie=UTF-8

http://mrhaki.blogspot.com/2012/06/gradle-goodness-working-with-live-task.html

I succeed to solve the problem using the following lines


    task taskX  {


       doLast
      {
        println 'taskX'

      }
    }
    taskX.dependsOn {
       tasks.findAll { 
          it.name.startsWith('lib') 
       }
    }
    task lib1  {

          doLast
      {
        println 'lib1'

      }

    }
    task lib2  {


          doLast
      {
        println 'lib2'

      }

    }
    task notALib  {


          doLast
      {
        println 'notALib'

      }

    }



