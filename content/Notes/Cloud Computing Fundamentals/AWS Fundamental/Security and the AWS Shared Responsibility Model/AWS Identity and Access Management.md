# AWS Identity and Access Management


---
### Notes and Ideas:
[[root user]] authorized [[Notes/Cloud Computing Fundamentals/IAM user]] to  graind permision for certain task


Example of IAM policy
```
{
	"Statements" :[{
	"Effect" :"Allow"
	"Action":"ec2:RunInstances",
	"Resource":<Amazon Resoucre Name here>
	"Condition":{
	
		<condition>		}
	
	
	}]

}
```
Attch to a user or a group of user 

---

### Key words:

---
#### TAGS