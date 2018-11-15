- title : FAKE it 'til you make it
- description : Introduction to F# Make 5 for the Austin F# Meetup's November meeting
- author : Chester Husk
- theme : night
- transition : default

***

## FAKE it 'til you make it
![FAKE logo](https://fake.build/assets/img/logo.svg)
<br />
Chet Husk 
<br />
[@chethusk](https://twitter.com/chethusk)
<br />
[GitHub](https://github.com/baronfel)

*** 

### Agenda

* Community Bulletin
* Who am I?
* What is FAKE?
* Why FAKE?
* Examples 
* Q&A

***

### Community Bulletin

Recent Events in the F#/.Net Ecosystem

* [FableConf/RemmiDemmiConf 2018 Videos](https://www.youtube.com/watch?v=Ry4qQxU0380&list=PL4vOF1DmOhsmzsCd1ghrey7sASjOngnOt) came out
* Dave Thomas ([@7sharp9_exhumed](https://twitter.com/7sharp9_exhumed)) started a [short-form video series](https://www.youtube.com/watch?v=CwQG0i-ah3U&list=PLIH3o_QrxxcfaVkNQGv2nurs44_TW3vIS) going over the design and usage of F# language features. Not just F#, too!
* [Anonymous Records](https://github.com/fsharp/fslang-design/blob/master/FSharp-4.6/FS-1030-anonymous-records.md) were merged in for F# 4.6!
* For the Visual Studio users, 15.9 released with many [F# tooling fixes](https://docs.microsoft.com/en-us/visualstudio/releasenotes/vs2017-relnotes#f)
* The online [Fable REPL](https://fable.io/repl/) has the Tour of F# tutorials on it

---

### Useful Community links

* Sergey Tihon's [F# Weekly newsletter](https://sergeytihon.com/category/f-weekly/)
* The F# Software Foundation [Community forums](https://forums.fsharp.org/)
* The F# Software Foundation [Slack channel](https://fsharp.slack.com/) - ~2300 members strong!
* The F# Software Foundation [Merch site](https://www.zazzle.com/fsharporg/gifts)
* The F# [Subreddit](https://www.reddit.com/r/fsharp/)

***

### Who am I?

* F# Foundation Board Member
* Web/Backend Developer at <img style="border: none; margin: 0px; height: 30px; vertical-align: middle;" src="/images/bds_logo.png"/> [Binary Defense Systems](https://www.binarydefense.com/)
* Microservices/k8s/devops background
* Jack of all trades
* Type Provider Dabbler
* Run this meetup

***

### What is FAKE?

--- 

### What _was_ FAKE?

## V4

* Build tool
* Task orchestrator

---

### What _was_ FAKE?

Example usage: [Paket](https://github.com/fsprojects/Paket/blob/master/build.fsx)

---

### Fake V4 Problems

<p class="fragment">Monolithic</p>
<p class="fragment">Required a Mono/.Net Framework tool</p>
<p class="fragment">Inconsistent API</p>
<p class="fragment">Required out-of-band dependency management</p>
<p class="fragment">CLI was confusing and hard-to-parse</p>

---

*** 

### What _is_ FAKE?

---

### FAKE 5 Design Goals

<p class="fragment">Lightweight Runner</p>
<p class="fragment">Integrated Dependency Management</p>
<p class="fragment">Pay-for-what-you-use</p>
<p class="fragment">Consistent API style</p>
<p class="fragment">Consistent CLI</p>
<p class="fragment">Compile and cache scripts</p>

---

### Introducing FAKE 5!

![fake5 splash](/images/fake5_splash.png)

***

### Fake 5 Benefits

---

### Cross-platform usage

#### System-level

* .Net Core global tool
* Chocolatey or .deb package

<br><br>
#### Project-level

* .Net Core local tool
* dotnet SDK Project-level tool
* paket-managed project level tool

---

### Integrated Dependency Management

Use a paket header to make your scripts self-contained

* Reference an existing paket.dependencies group

```fsharp
#r "paket: groupref FakeDeps //
```

* Declare a set of dependencies inline

```fsharp
#r "paket:
nuget Fake.Core.Target
nuget Fake.BuildServer.GitLab //
"
```

---

### Integrated Dependency Management

How does this work?

<p class="fragment">It's using a syntax similar to <a href="https://github.com/Microsoft/visualfsharp/pull/5850">what's coming</a> for FSI itself</p>

<p class="fragment">The syntax is pluggable, allows for different resolvers (paket, nuget, API references, precompilation, etc)</p>

---

### Pay for what you use

Because you're including only the dependencies you care about, it's no longer a huge package download

---

### Consistent API style

There are now [API Design Guidelines](https://fake.build/contributing.html#API-Design) for modules to make them more consistent.

* Consistent Module names: 
 * Fake.ILMergeHelper -> Fake.DotNet.ILMerge
* Consistent casing: 
 * ILMergeHelper.GetArguments -> Fake.DotNet.ILMerge.getArguments
* Consistent usage patterns
  * Modules typically have some sort of Options type with modification functions, as well as a run equivalent.
  * You get a sense of consistency across modules, which helps the more you use FAKE

---

### Consistent CLI

The FAKE 4 CLI made no distinction between arguments, environment variables, build targets, etc.
```
-------------------
 FAKE usage
-------------------

    fake.exe [<scriptPath>] [<targetName>] [options]

    scriptPath: Optional.  Path to your FAKE build script.  
                           If not specified, FAKE will use the first 
                           .fsx file in the working directory and fail 
                           if none exists.

    targetName: Optional.  Name of the target you wish to run.  
                           This will override the target you specifed to run 
                           in the build script.
                           When targetName is equal --listTargets 
                           or -lt FAKE will list the targets with their dependencies.

    Options:
```

--- 

### Consistent CLI

The FAKE 5 CLI is more structured and has much more detail

--- 

### Compile and cache scripts

FAKE 5 will compile your fsx scripts and only recompile when the source changes.
This opens up new use cases for fsx scripts (especially with a global tool install).

* System utilities
* Administration helpers
* Developer shortcuts

*** 

### Getting Started

* Check out the [tutorials](https://fake.build/fake-gettingstarted.html) for detailed info.
* Use the [dotnet SDK template](https://fake.build/fake-template.html) to bootstrap
  * it's not destructive so, run it on your existing projects

***

### Q & A

***

### Things to check out

* The new, improved [FAKE docs](https://fake.build)
* Our [associated meetup groups](https://southcentralcommunity.com/regions/Austin/)
