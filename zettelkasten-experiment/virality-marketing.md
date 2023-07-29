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

![](data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAARgAAAArCAIAAAAsdQBsAAAEzElEQVR4nO2dbbKzLAyGmWFXTN/tZFwOXcs7xa10dCstPD8Q5CPaVujRYq5fPdUijdxJCB7KDEEQxbC9O0AQC4xSCDnWa2+4Xjio5/NZr8kZEhJxSBAVKWCgylrVfSfk+A0pkZCII6IgltEoBXMURBWtByvQ6lIiIRHHA0vqaiV6XwpKJCTicKCaSWPUVrTuK7UUQUIiDgemmWmCNEqpTFFi9qXsjoREHI2FgMQYY2wllgzXS56z6b7jDNQjkk3fcVCPutkdCYk4Ghurc4mQtO6BMyaEICERp6SOkCx6uAqeCgk9sxASEnE0IiGxVZ7Ppx6ugidvC3mflIMKqe+4kHcSEtE2X49IlNoRjTCVDqbawbzaCspsXjH6SyFpfQMu5P3h2yAhEbuggAVxR0FYkNsWknIh9R0Psz17SOtBCiipoQ/X/zhjjMH/j4d/k4RE7MEohRdLrptXi69a95DFmTfRw7XkEYlbx4W8PxRwTkIi9sbpaJSCYdEnUVKc+41yri58/txdlZKdvnUkJGJ/3BxpcYV1tOnX9NLPpcCevVkMJaEsaoeERBwAN0GKp0YxTkpY6aHvLtue8RmuF1AmLUjoQWYV9GBu9cgvREIiDkAYY/DUzqKAgVLgtObzPWWjyqfP3VVcPiIhEfsz68ik1TsMnwb60xTwqBD395CQiN1JotBrJR0Qfev4GdaRIp/n+Mk79oegRvPUsp4vwE2NuXjzK3dG3zrOkUlUe0JaHQ8kJpx1ETnIest4Ic0FyR9yDzmvHy+ZJ6/lNGu0YIuE+GvVtF5TMGMms30w/csI16l3Jb3PWMcqdbZdowVfJq+qHabXB4OZvJofLIa9yVFi/sqQWDtr46VOYbRsqYdiEgpbWhWbgnvgmGL3O0f+KL+JPhDnBvY8UNGjv+ncM7r4fM30s6CybphsaGIdc62XjoVmjZZ+tSwmrVrvc3fSCmxlTSz1TPP9cYZ0jxvGNyNsMUqAwnE2vbaHonsXfDx96dfD7ehAupHcYtzr4041HMcJ2N5QzRoNcUep0HDr2cuAqr5F6i+wTUir4zVxWcGfiytx4YH44/6ymSPEu1EgpE9o2WjbhDQdEALzOwFLvurnWXngaWFMmLz4X3tMxHhnjOxhu9yNhXcWmvqUho22ObWzgRQAzhaNjDGGpeUnMye6y2PCn4fl2Ynpy5yrQZpBjkwtvV1swKLJJ6ldy0aLu4LqDLeekKNRAKqGo/o5mDGTk4qcW+rPgjPiNDs5U4GQYzTIQv/21piIb6RPt9O7g3UDHxRzx+b3KsyI2zZakBt+Uv4+c7HBElWR8oTBlZmEHKMzw5ua5gupN/fv2enofDQ8kH48KkDhp7DEleeDIjqjYvm2VaMhbX3Bem3R5iNCi16RlhNx3rPL3tablwDutjfcuYTCnUx64PMOXttoT0jGLJQCFusDhDHmlX2OYb0pIZ22Mek7zkoFMFwvfBJjUc/aFBLRJi4kPq2Kin9+z/6rn1HASUjEeXA6GqXgrN6PWPqN9ksgIRE/Q1gCuddrloREnApXsVewNDV6tY0JPpsiIRFnYl4Uo9SOILYSLi6jPx+2GRIScR6iZyzsj4jV+kWJKmV0EhLxAyT/gaXd9vilS7HhNvvTPArZDvId/gEJgBo8ymU1DgAAAABJRU5ErkJggg==)
_[source](https://www.innojazz.com/2013/01/how-to-forecast-viral-growth-of-your.html)_

Observations:

* Lowering the amount of time it takes for a user to invite other users to the service may be substantially more effective than increasing the viral coefficient. Lowering `ct` increases the power whereas increasing `K` only increases the base.
* The number of cycles the invite process has gone through is represented by `t/ct`.

Example: with `Customers(0) = 10`, `K = 2.0`, `ct = 5.0 days`, after 20 days go by, how many users would you have?

```code
Customers(t) = Customers(0) * (K ^ (t / ct + 1) - 1) / (K – 1)

Customers(20) = 10 * (2.0 ^ ( 20 / 5.0 + 1) - 1) / (2.0 – 1)

Customers(20) = 10 * (2.0 ^ 5 – 1) / (1.0)

Customers(20) = 10 * 31

Customers(20) = 310
```

## Expanded forecasting model

The model above is a very simplified approach to viral forecasting and, therefore, has some drawback. The model does not take into account:

1. User attrition, i.e. churn
2. User saturation, like viral diseases: infectors at a certain point in time start to meet more and more infectees as time goes by.
3. Market size, there will be a limited number of people in the market you're targeting.

Without these elements factored in, the basic model will show exponential growth. However, an S-shaped growth curve is more realistic, as virality will decay over time.

## Sources

* [Viral Marketing](https://www.marketing-schools.org/types-of-marketing/viral-marketing.html)
* [Viral Hero: How To Build Viral Products, Turn Customers Into Marketers, And Achieve Superhuman Growth](https://www.amazon.nl/Viral-Hero-Customers-Marketers-Superhuman/dp/1948080958)
* [How to forecast viral growth of your mobile app](https://www.innojazz.com/2013/01/how-to-forecast-viral-growth-of-your.html)
* [Lessons learnt viral marketing](https://www.forentrepreneurs.com/lessons-learnt-viral-marketing/)
* [A Virality Formula](https://kevinlawler.com/viral)
* [Network Saturation, Viral Decay, and the Peaks and Valleys of Growth](http://viralhero.com/viral-marketing-projections/network-saturation/)

[[statistics]]