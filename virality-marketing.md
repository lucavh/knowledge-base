# The Math of Virality Marketing
_Viral marketing_ is a business strategy that uses existing social networks to promote a product. The basis of viral marketing is in the spread of information by word-of-mouth (i.e. word-of-Mouth marketing), but modern technology has allowed the viral effect to include many Internet-based platforms as well. 

The key element of viral marketing is to offer your existing customer base an incentive to refer new customers from their own network. This is also referred to as "referral marketing" or "member-get-member marketing". 

There are several key metrics which provides insights into the viral growth. Based on these metrics, it is then possible to project the impact of virality, and this predict the impact of viral campaigns, over a fixed period of time in the future. 

## Key Performance Indicators

### K-factor
|KPI|Description|
|--|--|
|**K** |The viral factor, a measure of the **magnitude** of a product's virality. This is the average number of new customers each existing customer will successfully onboard to the product to enter the viral loop. Calculation: `K = i * conv%`. |
|**i**|Total number of invites send out per user on average during one cycle of a viral loop. i.e. over a fixed period.|
|**conv%**|The conversion rate on the invites send out (the percentage of those invites that result in a new prospective customer).|

Example: if`K = 0.5`, every customer will bring 0.5 prospective customers into the viral loop for you. When K is equal to or above 1, a product goes viral. This is very hard to reach and if reached, it wil not last for long. 

Both  `i`  and  `conv%`  are incredibly important viral metrics to consider when performing viral optimization. Questions to ask when optimizing these metrics:

* Which viral channel yields the highest  `i` ?
* Which viral channel yields the highest  `conv%`?
* Are there certain segments of users where  `i` or  `conv%`  is higher? Lower?

### Amplification factor
|KPI|Description|
|--|--|
|**A**|A multiplier that indicates how many total customers you can expect to acquire for every one user you acquire from non-viral means **after viral marketing does it's job**. Calculation: `A = 1 / (1-K)`.|

Business value: with a K factor below 1, you'll need to continuously acquire traffic through non-viral means in order to contunually allow your viral loop to do its thing. **But**, with a strong A factor, you'll have a huge advantage in comparison to your competitors with an unoptimized viral loop, because you'll now have a significant discount on your ad spend. Example: if `A = 1.3`, for every 1 customer you acquire via non-viral means, you can expect 1.3 users in total after viral marketing is all said and done. 

## Viral Cycle Time

|KPI|Description|
|--|--|
|**ct**|Viral Cycle Time, the time it takes to complete the viral loop, i.e. from becoming a customer to inviting a new customer. This is the single biggest factor in determining the growth over time. Usually measured in days.|

## Projection Formula for Viral Growth over Time

|Variables|Description|
|--|--|
|**customers(0)**|The number of active customers at the start.|
|**t** |The number of days in the future for which you want to make a prediction.|
|**customers(t)**|The number of active customers at time `t`.|
|**K**|The viral coefficient, i.e. the average numer of successful invites per active user.|
|**cv**|The Viral Cycle Time, i.e. the time it takes from the moment a customer becomes aware of your product (i.e. becomes customer) until the moment they send their first invite. Measured in the same time unit as `t`.|

### Basic formula
```
u(t) = u(0) * ((K ^ ((t / ct) + 1) - 1) / (K - 1)) 
```

Example: with `u(0) = 10`, `K = 2.0`, `ct = 5.0 days`, after 20 days go by, how many users would you have?
``` 
u(t) = u(0) * (K ^ (t / ct + 1) - 1) / (K – 1)

u(20) = 10 * (2.0 ^ ( 20 / 5.0 + 1) - 1) / (2.0 – 1)

u(20) = 10 * (2.0 ^ 5 – 1) / (1.0)

u(20) = 10 * 31

u(20) = 310
```


## Sources
* [Viral Marketing - Marketing Schools](https://www.marketing-schools.org/types-of-marketing/viral-marketing.html)
* [Viral Hero: How To Build Viral Products, Turn Customers Into Marketers, And Achieve Superhuman Growth - Book](https://www.amazon.nl/Viral-Hero-Customers-Marketers-Superhuman/dp/1948080958)
