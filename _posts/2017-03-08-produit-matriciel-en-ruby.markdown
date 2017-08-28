---
layout: post
title: "Produit matriciel en Ruby"
date: 2017-03-08 12:50:43 +0100
author: jeremy
comments: true
categories: blog
---

```ruby
def produit_matriciel
  mat1 = [[2, 8, 6], [2, 7, 2], [1, 3, 9]]
  mat2 = [[7, 9, 6], [5, 6, 4], [1, 4, 3]]
  matRes = []
  # Faire tests si mat1 a moins de colonnes que mat2 a de lignes alors pas possible
  for j in 0..mat1.count - 1
    arrayTemp = []
    for k in 0..mat2[0].count - 1
      temp = 0
      for i in 0..mat1[0].count - 1
        temp += mat1[j][i] * mat2[i][k]
      end
      arrayTemp << temp
    end
    matRes << arrayTemp
  end
  matRes.each do |i|
    puts i.inspect
  end
end

produit_matriciel
```
<!--break-->
