#EFS
---

-	📒 [Homepage](https://aws.amazon.com/efs/) ∙ [User guide](http://docs.aws.amazon.com/efs/latest/ug) ∙ [FAQ](https://aws.amazon.com/efs/faq/) ∙ [Pricing](https://aws.amazon.com/efs/pricing/)

### EFS Basics

-	🐥**EFS** is Amazon’s new (general release 2016) network filesystem.
-	It is similar to [EBS](#ebs) in that it is a network-attached drive, but it [differs in important ways](https://aws.amazon.com/efs/details/#When_to_Use_Amazon_EFS_vs._Amazon_EBS):
	-	EFS can be attached to many instances (up to thousands), while EBS can only be attached to one drive. It does this via [NFSv4](https://en.wikipedia.org/wiki/Network_File_System).
	-	EFS can offer higher throughput (multiple gigabytes per second) and better durability and availability than EBS (see [the comparison table](#storage-durability-availability-and-price)), but with higher latency.
	-	EFS cannot be used as a boot volume or in certain other ways EBS can.
	-	EFS costs much more than EBS (up to [three times as much](#storage-durability-availability-and-price)).

🚧 [*Please help expand this incomplete section.*](CONTRIBUTING.md)

