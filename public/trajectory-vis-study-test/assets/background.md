# Background Information

## t-SNE
t-Distributed Stochastic Neighbor Embedding (t-SNE) is a dimensionality reduction technique
commonly used to transform high-dimensional data into 2 dimensions and visualized in 2D scatterplots, 
allowing users to analyze the relationship between data points. 
The reason why t-SNE works is that points that are close to each other in high dimensions are also close in 2D after its processing.
We call the 2D results a _embedding_.
t-SNE runs iteratively during which the embedding is optimized.

Below is an example t-SNE _final_ embedding, which is commonly used in various visual analytics tasks 
through inspecting the neighborhood relationships of points.

<img src="./assets/t-SNE_final_embedding_example.png" width="500" height="auto">

Beyond analyzing the _final_ embedding, some tasks can be done by analyzing the intermediate states of the embedding, 
i.e. the optimization process of t-SNE, or t-SNE _dynamics_. 
Below is the typical workflow of a [recent research](https://rupress.org/jem/article/215/5/1383/42593/Mass-cytometry-reveals-innate-lymphoid-cell) 
which analyzed the data dynamics of t-SNE optimization: 
the researchers used animations or snapshots during the optimization for further analysis to gain insights. 
Snapshots look like this:

<img src="./assets/t-SNE-6stages.png" style="width: 90%; height: auto;">

If we take many snapshots and make an animation, the optimization will look something like this:

<img src="./assets/Example-Animation-ezgif.com-speed.gif" style="width: 60%; height: auto;">

However, this requires going over the snapshots of embeddings to check what the data in question is like at that point, 
which is usually a cumbersome process. This inspired us to design 
visualizations that present t-SNE dynamics in one visualization with all the visual elements needed.

only two views: a 2D t-SNE trajectory view and a 1D t-SNE trajectory view 
enhanced by a bundling technique, among some other design choices.

## Our Research
In the 2D view, both the horizontal (X) and vertical (Y) axis are used 
to represent embedding positions. Points usually originate from the center and expand outwards, 
with the amount of movement between iterations being different. In our questions, the 2D view will look like this:

<img src="./assets/2D-Example.png" width="500" height="auto">

Inm the 1D view, the horizontal (X) axis is encoded with the actual iterations, 
so you can expect the step size at the X-axis to be the same. Points originate from the left and move towards the right 
of the view as the T-SNE algorithm progresses. In our questions, the 1D view will look like this:

<img src="./assets/1D-Example.png" width="500" height="auto">

In this questionnaire, we will test the effectiveness of the above-mentioned two views on a number of tasks,
as well as the t-SNE animations as the traditional method for comparison.

Note that we will not color the data in such a complex way in the questionnaire. Rather, data items that you should focus on are randomly colored while the others will be uniformly colored in light gray. The order of questions are given randomly too.  

## Additional Info for Questions
In the questions, we often ask you about the "split" behaviour of data, since data points can share trajectories during some iterations and start to separate during others.
Such behaviour can happen early or late. Major differences between data usually make them split early while minor differences usually make them split late.
An example of splitting in the 2D view is given as follows:

<img src="./assets/questions/split_2D.png" width="800" height="auto">

An example of splitting in the 1D view is given as follows:

<img src="./assets/questions/split_1D.png" width="800" height="auto">

In some questions, we will mention "phases". Please consider phases as equal number of iterations. For instance, when we talk about 
"the earlier phase" and "the later phase", the former represents the first half of all iterations and the latter represents the second half of all iterations.
In the 1D view, you can tell exactly how early or late the iteration phase is, because iteration is encoded in the x-axis; 
In the 2D view, however, you cannot tell directly which iteration phase a trajectory is at, given a certain position, because the data point moves at different rate every iteration.

## Start Answering Questions
Click **Start** button when you are ready to start. 