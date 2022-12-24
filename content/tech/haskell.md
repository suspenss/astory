+++
 title = "haskell 学习笔记 vol.0" 
 date = "2022-12-24T21:40:48+08:00" 
 tags = ["haskell"] 
 slug = "haskell"
 gitinfo = true
 align = false
+++


```` haskell
min :: Ord a => a -> a -> a
max :: Ord a => a -> a -> a

"abc" == 'a' : 'b' : 'c' : []
````

函数调用拥有最高的优先级

``` haskell
doubleMe x = x * 2
doubleUs x y = doubleMe x + doubleMe y
doubleSmallNumber x = if x > 100
                      then x
                      else x * 2
doubleSmallNumber' x = (if x > 100 then x else x * 2) + 1

lucky :: Integral a => a -> String
lucky 7 = "LUCKY NUMBER SEVEN"
lucky _ = "sorry, you are out of lucky"

-- factorial recursion version
factorial :: (Integral a) => a -> a
factorial 0 = 1
factorial n = n * factorial (n - 1)

-- factorial product function version
factorial' :: Integral a => a -> a
factorial' x = product [1..x]

point_add :: Num a => (a, a) -> (a, a) -> (a, a)
point_add (a, b) (c, d) = (a + c, b + d) 

head' :: [a] -> a
head' [] = error "error"
head' (x: _)  = x

length' :: Num a => [b] -> a
length' [] = 0
length' (_: xs) = 1 + length' xs

sum' :: Num a => [a] -> a
sum' [] = 0
sum' (x: xs) = x + sum' xs

bmi_tell :: (RealFloat a) => a -> a -> String
bmi_tell weight height
    | bmi <= 18.5 = "underweight"
    | bmi <= 25.0 = "normal"
    | bmi <= 30.0 = "fat"
    | otherwise   = "whale"
    where bmi = weight / height ^ 2

bmi_tell' :: (RealFloat a) => a -> String
bmi_tell' bmi
    | bmi <= 18.5 = "underweight"
    | bmi <= 25.0 = "normal"
    | bmi <= 30.0 = "fat"
    | otherwise   = "whale"

calcbmis :: RealFloat a => [(a, a)] -> [a]
calcbmis xs = [bmi w h | (w, h) <- xs]
    where bmi weight height = weight / height ^ 2

calcbmis' :: RealFloat a => [(a, a)] -> [a]
calcbmis' xs = [ bmi | (w, h) <- xs, let bmi = w / h ^ 2 ]

-- fib =  fib(n) = fib(n - 1) + fib(n - 2)
fibs :: [Integer]
fibs = 1 : 1 : zipWith (+) fibs (drop 1 fibs)
```