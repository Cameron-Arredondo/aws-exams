# AWS Architecting & Ecosystem

## AWS Whitepapers Well-Architected Framework
- Test systems at production scale
- Automate to make architectural experimentation easier (terraform, CDK)
- Allow for evolutionary architectures
- Drive architectures using data
- Improve through game days
    - simulate applications for flash sale days

## Design Principles Best Practices 
- Scalability: Vertical (get a bigger EC2 instance) & Horizontal (create more EC2 instances) 
- Disposable Resources: servers should be disposable & easily configured
- Automation:  Serverless, Infrastructure as a Service, Auto Scaling
- Loose Coupling:
    - Monolith are applications that do more and more over time, become bigger
    - Break it down into smaller loosely  coupled components
    - A change or a failure in one component should not cascade to other components
- Services, not servers


# Well Architected Framework 6 Pillars
## Operation Excellence
- PERFORM OPERATIONS AS CODE IaC > ClickOps
- Annotate Documentation - automate the creation of annotated documentation after every build

## Security
## Reliabilty
## Performance Efficiency
## Cost Optimization
## Sustainability
