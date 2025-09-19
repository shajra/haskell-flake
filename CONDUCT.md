# Conduct and Code Development

## Ethical reasons for forking

The upstream documentation for this project has some links that lead to a larger
personal site at https://srid.ca.  This personal site hosts the author's
personal notes, some of which have childish right-wing screeds regarding
"wokeness," among other troubling topics.  I am compelled to warn users of the
adjacency of such writings with otherwise relevant technical documentation.

Additionally, the upstream project has a "harmlessness" code of conduct that
seems more concerned with providing safety for those with repulsive views of
fellow users and collaborators.  Even if I am extrapolating intent, in light of
recent world events I have reasons to justify my inference.  More explicitly,
the tone of the code misses the point of why these codes came to exist in the
first place.

## Why such a feeble fork?

From a technical perspective, I agree with a most of the decisions made by the
upstream project.  And much of the purely technical documentation is useful.

Recreating all this work may create an improved separation from the upstream
author's politics, but would involve time and effort that I don't have now and I
don't foresee having any time soon.

## Get the upstream author to change?

I don't know the upstream author and have had no contact (in person or online)
with him.  Though I can be diplomatic and friendly, even with those I disagree
with, the level of vitriol in the upstream author's writing leaves me with
insufficient hope for a productive conversation.

However, a simple change that would help would be the complete separation of
project documentation from the author's personal site.  This would even align
with the author's "harmlessness" code of conduct.

I have no authority to assert that the author must make this change.  It's his
right to publish his documentation however he wants.

The only clear right I have is to fork the project.

## Are there alternatives?

Alternatives exist, but none that satisfy the same ergonomic goals.

A fundamental goal is to have a user experience that easily extends to expert
users, but that also caters to beginner users who might be overwhelmed by
figuring out the complexities of authoring Nix expressions.

Towards this end, I think that [flake-parts](https://flake.parts) is a good
idea.  It not only removes a good deal of boilerplate from `flake.nix`, but also
allows users to mix in different functionality with the well-established and
"declarative" NixOS module pattern.  To me, it makes sense to build Haskell
projects on top of this.

I know many respectable Haskell+Nix developers prefer using small Nix
expressions in a vanilla `flake.nix` file.  But that gives beginners no helpful
hand for all the tool integrations that beginners might need even more than
experts (such as IDE integration, linting, and formatting).  It's too easy to
end up copying/pasting code until you have a complex `flake.nix` that makes Nix
and flakes both look bad.

## Is there a replacement code of conduct?

While I find the upstream author's public statements troubling, I also find
codes of conduct approximating a legalistic language counterproductive.

Ultimately, someone with administrative/moderator privileges makes authoritative
decisions in the context of all of these open-source projects.  Small
open-source communities don't have the social machinery to extract actionable
sound judgements from these inevitably imprecise codes. At best, these documents
can signal our intent.  But that intent exists outside the precision of written
rules.  It's in the tone of the authorship.  A queer-friendly coffee shop
accomplishes a lot by displaying a pride flag.  They don't need to put up a faux
legal document explaining the circumstances under which they kick out bigots.

If you come from a historically disenfranchised group, I want you to know that I
*believe* that systemic oppression is real and that it is a problem. I want you
to be able to trust that those in authority have a commitment to the hard work
required to recognize implicit biases and compensate for them.  That trust is
built incrementally through the work.

Everyone should feel free to express their race or gender publicly in any civil
way they wish without bearing on their technical contributions.  This is a
fundamental human right.  There should be no doubt of an project maintainer's
support.

I also want to make clear that it's okay if people who disagree with such
inclusion feel uneasy.  Feeling uneasy about such an expression is not violation
of a human right.

Furthermore, even if changing words like "master" to "main" are more symbolic
than substantive, why resist?  Just do it.  It showcases some empathy and sets
the right tone for inclusion, all at a negligible cost.

I don't know if my statements above can sufficiently offset the upstream
author's repulsive views.  But it's my best attempt to begin a process of
building trust, which I find codes of conduct insufficient at building.

This is just a personal project.  For now, I make all the decisions on it.  You
are welcome to collaborate with me.  Hopefully, this document gives you the
confidence to do so.  At the least, I hope you have gotten my warning about the
upstream author's writings and a sense of shared values with me.

Haskell and Nix are nice.  A commitment to correcting for historic and
continuing suppression of essential human dignity is more important.
