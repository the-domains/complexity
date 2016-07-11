---
author: []
dateModified: '2016-07-11T00:50:58.743Z'
datePublished: '2016-07-11T00:51:10.904Z'
description: >-
  I created a simple model of world order developing. It's too basic to prove
  anything and there is no underlying data. However, it is useful as a
  demonstration of a few concepts that are foundational to the rest of my
  research project. In fact, this might better be described as an animated
  diagram of how ideas relate to each other.
hasPage: true
inFeed: true
inNav: false
keywords: []
title: ''
starred: true
sourcePath: _posts/2016-07-11-first-step.md
url: first-step/index.html
_type: Article

---
I created a simple model of world order developing. It's too basic to prove anything and there is no underlying data. However, it is useful as a demonstration of a few concepts that are foundational to the rest of my research project. In fact, this might better be described as an animated diagram of how ideas relate to each other.

This simulation is an adaptation of Cioffi-Revilla's 'canonical theory' of (origins and development of) social complexity \[1\]. It is a model of the process of organization in the world system, rather than being a model of countries or institutions or wars. Anybody can examine the code and experiment with the simulation by downloading the_[.nlogo][0]_ file from my simple-world-systems repository on GitHub.

The model narrative goes like this:

Imagine that there are some states (between 5 and 40, using the num-states slider). I represent those states as brown dots arranged in a circle. The states are all the same except for the the amount of wealth they possess (by any measure), the minimum amount of resources they are willing to have and their ability to produce more resources. As time passes some states will start a war with one or more other states. This model does not consider _why_ the war starts, just that it _may_ start. The probability of a war starting is adjustable (initial-prob-war).

Time is measured in 'ticks' but this model does not define how long a 'tick' would be in the real world. One state gets a chance to start a war in each tick. If a state starts a war with a state who is already at war, they can start a new war or join the existing war. The model does not identify sides in the war, just that those states are all involved in a war together. We call each new war a new 'process' of interaction, not because I am claiming that the real world works that way but just as a way to describe processes that begin with war.

I represent a new process with a green dot and a war with an orange link from the state to the process. Each new process gets counted in the 'New Process' monitor, so that we can keep track of how many processes get started. Each state involved in a war process must spend resources on the war each tick of the model while the war goes on. The 'In Conflict' monitor shows how many processes represent active wars.

In the next tick after a war starts, the states involved in a war process have a chance to decide that they need peace instead, depending on a mixture of chance and the the ratio of their current resources to the minimum amount of resources they're willing to have. As their resources dwindle, the chances that they will want peace increases. The process only progresses if every state involved agrees that they need peace. If a state spends all of their resources waiting for other war participants to want peace, the state is destroyed (and immediately gets replaced by another state). The 'See Need' monitor shows how many processes there are, where all (currently) involved states perceive a need to stop the war.

Even when states have not decided that they need peace, the war may stop anyway. In this case, the states haven't "learned" to cooperate. The war just stops. In this case, the process dies.

Similarly, just because all of the states want the war to stop does not mean that the war will stop. So, the process goes through another iteration in which all the states have to agree to undertake some action to stop the war. If all the states agree to undertake action to stop the war (enter into a peace process), they form an institution. The 'Trying' monitor keeps track of how many active processes there are where all of the states have agreed to undertake action. States involved in these processes are still at risk of running out of resources.

I did not include a monitor for how many 'New Institutions' get created, but there is a monitor for how many institutions currently exist. I represent institutions with a blue dot. A grey arrow shows which process spawned the institution and thin grey arrows show which states are members of the institution. Institutions have an increasingly pacifying effect on states, so the chances that they will start another war with another member of the institution become smaller and smaller as time goes on. The cumulative amount by which all institutions reduce the probability of war among their members is represented as the blue line in the Probability of War plot. Each time a new institution is formed, the overall probability of war also declines a tiny bit (0.1%). States must contribute resources to a process every tick once they have agreed to undertake action.

If a new war does break out between members of an institution, their institution dies. States must contribute a small amount of resources to the institution. If they do not, either they lose their membership or the whole institution dies.

Forming an institution does not guarantee that the war will stop, either. The model gives the peace process a 50/50 chance of success---just for convenience, not because of any data on the success rate of real-world peace processes. The 'At Peace' monitor shows how many processes have become peaceful.

If peace lasts for ten ticks, the process dies and only the institution remains. Once the institution provides it's members a reduction in probability of war greater than the overall probability of war, the institution 'stabilizes' and gets counted in the 'Stabilizing' monitor.

If an institution has been stable for 50 ticks, it is no long relevant and it dies. The simulation stops when there has been 50 ticks with no change in probability of war or the overall probability of war is less than 0\.

The model always ends with universal peace. There is no process that 'reverts' to an earlier stage. All processes progress or end/die and all states decide on peace or they are destroyed.

[This movie][1] of one simulation run starts with me clicking \`setup\`, which initializes the simulation and arranges several dots in a circle. The dots represent states in the world system. The states are identical, except for the amount of resources they hold and their productivity. When the simulation starts (click \`go\`) NetLogo randomly choose a state and asks it to pick a target state and consider war, with some probability. The initial probability of war can be manipulated with a slider. This process repeats with every tick of the model.

If a state starts a war, the model creates a new 'process' (green dot) and each state involved adds the process to their list of current wars. The war appears as orange lines linking the states to the process. Other states that target either warring state during a subsequent turn may either join that war or start a new one. Each war costs a random amount of resources each tick. This represents condition C from the canonical theory, "a situational change occurs".

In subsequent ticks, each on-going process will check with participating states whether they need peace (combined probability and resources) then whether they will undertake action (another combination of probability and resources). If states do not recognize the need for peace before their resources are gone, they die and get replaced by a new state. If they do not undertake action and the war persists (simple probability) then they may die and get replaced by a new state. If state recognize their need for peace and undertake action, a new institution is formed by the process. The institution consumes small resources and may or may not pacify the process (the link becomes green). They also lower the probability of war for their members. States must maintain the cost of the institution in subsequent turns. If they do not (or cannot) then they risk losing membership in the institution or the institution dissolves (along with its process) and the states revert to their original condition.

During each turn that a peaceful process persists, the links to the institution thickens and the states' links to the institution thickens. When the links are fully formed, the process dies and the institution remains. If the institution's pacifying effect has kept the probability of war below zero for too long, the institution stagnates and dies.

Among other things, the monitors show the number of processes that have been created and the number that are in each decision state (not political outcomes). Many processes will form but few continue to become peaceful. Most of those form persistent institutions.

Depending on the settings, the simulation will typically run about 2,000-3,000 ticks before it stabilizes; though occasionally in as few as 200 ticks. It always stabilizes.

State resources were not strictly necessary but I added them to address a question (when I defended my proposal) on the role of economics in world order. There is no consideration of sociology in this model. In a previous attempt, I had included "population" agents as proxies for sociological aspects and the dimension of the model logic became cumbersome for the minimal working example.

\[1\] Cioffi-Revilla, Claudio. 2005\. "A Canonical Theory of Origins and Development of Social Complexity." _The Journal of Mathematical Sociology _29 (2) (April 1): 133--153\. doi:10.1080/00222500590920860\.

[0]: https://github.com/usuallycwdillon/simple-world-order/tree/master/net-logo-world-order
[1]: https://youtu.be/wPU-lvCRJyE