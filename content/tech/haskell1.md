+++
 title = "learn my haskell vol.1" 
 date = "2022-12-30T17:40:48+08:00" 
 tags = ["haskell"] 
 slug = "haskell1"
 gitinfo = true
 align = false
+++

note 1: some modules and codewars questions

``` haskell
import Data.List
import Data.Char

search needle haystack =
    let nlen = length needle
    in foldl (\acc x -> if take nlen x == needle then True else acc) False $ tails haystack

-- intersperse function
myIntersperse :: a -> [a] -> [a]
myIntersperse y = drop 1 . foldr (\x acc ->  y: x: acc ) []  

-- intercalate function
-- myIntercalate :: [a] -> [a] -> [a]
myIntercalate xs yss = drop (length xs) $ foldr (\as acc -> xs ++ as ++ acc) [] yss 

-- tanspose function
-- myTanspose

-- concat function
myConcat xss = foldr (\as acc -> as ++ acc) [] xss

-- a codewars question
findMidIndex :: (Num a, Ord a) => [a] -> Int
findMidIndex xs = length boollist 
    where taillist = tail . map sum . inits $ xs
          headlist = init . map sum . tails $ xs
          boollist = takeWhile (/= True) $ zipWith (==) taillist headlist

-- codewars
findNextSquare :: Integer -> Integer
findNextSquare n 
    | ispefect truen = truncate $ head $ filter ispefect [truen + 1..]
    | otherwise = -1
    where truen = fromInteger n

-- ispefect :: Integer -> Bool
ispefect x = fromIntegral (truncate . sqrt $ x)^2 == x   

--codewars
rowSumOddNumbers :: Int -> Integer
rowSumOddNumbers x = sum $ take x $ drop (sum [1..x-1]) [1, 3..]

-- https://www.codewars.com/kata/546e2562b03326a88e000020/train/haskell
squareDigit :: Int -> Int
squareDigit it 
    | it < 0 = negate $ proc (negate it)
    | otherwise = proc it
    where proc i = read (concatMap (show . (^2)) . intToListWithShow $ i) :: Int

-- 2 function about exchange a number into a list

intToListWithShow :: Int -> [Int]
intToListWithShow = everyToDigit . map show . show
    where everyToDigit  = map (\x -> digitToInt (read x :: Char)) 

-- pure mathmatic, so I think it has high perfermence
intToList :: Int -> [Int]
intToList x  = case x of
    0 -> [0]
    a | a < 0 -> reverse . toList . negate $ a 
    a -> reverse . toList $ a 
    where toList 0 = []
          toList a = mod a 10 : (toList . quot a $ 10) 

-- judge a number whether a prime
isPrime :: Integer -> Bool
isPrime x = case x of
    x | x <= 1 -> False
    2 -> True 
    _ -> all (\a -> mod x a /= 0) (2 : [ x | x <- [2..truncate . sqrt . fromInteger $ x], odd x])

-- compute the number of digits
countNumOfDigit :: Int -> Int
countNumOfDigit 0 = 0
countNumOfDigit x = 1 + (countNumOfDigit . quot x $ 10)
```