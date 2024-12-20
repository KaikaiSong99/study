# Background Information

## t-SNE
t-Distributed Stochastic Neighbor Embedding (t-SNE) is a dimensionality reduction technique
commonly used to transform high-dimensional data into 2 dimensions and visualized in 2D scatterplots, 
allowing users to analyze the relationship between data points. 
The reason why t-SNE works is that points that are close to each other in high dimensions are also close in 2D after its processing,
so users can analyze relationship between high dimensional data points by just looking at neighbouring points in 2D.
We call the 2D results a _embedding_.
t-SNE runs iteratively during which the embedding is optimized.

Below is an example t-SNE _final_ embedding, which is commonly used in various visual analytics tasks 
through inspecting the neighborhood relationships of points. As you can see, color encodings are often used along with the visualization. 
These colors are based on either clustering results or manual labelling. 

<img src="./assets/t-SNE_final_embedding_example.png" style="width: 40%; height: auto;">

Beyond analyzing the _final_ embedding, some tasks can be done by analyzing the intermediate states of the embedding, 
i.e. the optimization process of t-SNE, or t-SNE _dynamics_. 
Below is the typical workflow of a [recent research](https://rupress.org/jem/article/215/5/1383/42593/Mass-cytometry-reveals-innate-lymphoid-cell) 
which analyzed the data dynamics of t-SNE optimization: 
the researchers used animations or snapshots during the optimization for further analysis to gain insights. 
Snapshots look like this:

<img src="./assets/t-SNE-6stages.png" style="width: 90%; height: auto;">

If we take many snapshots and make an animation, the optimization will look something like this:

<img src="./assets/Example-Animation-ezgif.com-speed.gif" style="width: 40%; height: auto;">

However, this requires going over the snapshots of embeddings to check what the data in question is like at that point, 
which is usually a cumbersome process and poses high cognitive load to users. This inspired us to design 
visualizations that present t-SNE dynamics in one visualization with all the visual elements needed.

## Our Research
An intuitive way to do this is to record positions of points at all iterations and connect them into trajectories in the visualization.
We enhanced this idea by adding a modified bundling approach to reduce visual clutter while preserving key information in the visualization.
We call this visualization the _2D view_.
The 2D view looks like this:

<img src="./assets/2D-Example.png" style="width: 40%; height: auto;">

In the 2D view, the two dimensions are used to represent 2D embedding positions. 
Just as typical t-SNE, points usually originate from the center and expand outwards (see the blue trajectories for example),
with the amount of movement between iterations being usually different.

The 2D view has its limitations: we cannot tell where the point is at a given iteration because iterations 
are usually in number of hundreds and in each iteration the amount of movement is different. Therefore, tracking points are tricky.
We introduce another visualization to tackle it, called the _1D view_. It frees up one dimension in the 2D to encode iteration,
using only one dimension to represent t-SNE embeddings. We use 1D t-SNE here, which only have 1 dimension to represent embeddings, instead of 2D t-SNE: it is of lower resolution than the 2D t-SNE 
but can still capture neighbourhood relations of points. The 1D view looks like this:

<img src="./assets/1D-Example.png" style="width: 40%; height: auto;">

In the 1D view, the horizontal (X) axis is encoded with the actual iterations,
so you can expect the step size at the X-axis to be the same. Points originate from the left and move towards the right
of the view (see the gray trajectories for example) as the T-SNE algorithm progresses.

In the following questionnaire, we will test the effectiveness of the above-mentioned two views on a number of tasks,
as well as the t-SNE animations as the traditional method for comparison. 
We will color the data in a simpler and cleaner way in the questionnaire. 
Data items that you should focus on are randomly colored by groups while the others will be uniformly colored in light gray. 
The order of questions are given randomly too.  

## Additional Info for Questions
In the following questionnaire, we often ask you about the "split" behaviour of data, since data points can share trajectories during some iterations and start to separate during others.
Such behaviour can happen early or late. Major differences between data usually make them split early while minor differences usually make them split late.
Example of splitting in the 2D view and the 1D view are given as follows:

<img src="./assets/questions/split_2D.png" style="width: 35%; height: auto;">
<img src="./assets/questions/split_1D.png" style="width: 60%; height: auto;">

In some questions, we will mention "phases". Please consider phases as equal number of iterations. For instance, when we talk about 
"the earlier phase" and "the later phase", the former represents the first half of all iterations and the latter represents the second half of all iterations.
In the 1D view, you can tell exactly how early or late the iteration phase is, because iteration is encoded in the x-axis; 
In the 2D view, however, you cannot tell directly which iteration phase a trajectory is at, given a certain position, because the data point moves at different rate every iteration.

## Example Question
<img src="./assets/questions/q23.png" style="width: 40%; height: auto;">

Question: Which one of the following three classes splits first?

A. Orange

B. Red

C. Blue

D. I cannot answer

The answer to this question is **B. Red**, as we can see the orange and the blue were relatively close to each other in the early phase
while the red separates from them from the beginning.

## You Are Ready To Start
Click **Start** to begin answering questions!