+++
 title = "learn my haskell vol.1" 
 date = "2022-12-30T17:40:48+08:00" 
 tags = ["haskell"] 
 slug = "haskell1"
 gitinfo = true
 align = false
+++


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


findMidIndex :: (Num a, Ord a) => [a] -> Int
findMidIndex xs = length boollist 
    where taillist = tail . map sum . inits $ xs
          headlist = init . map sum . tails $ xs
          boollist = takeWhile (/= True) $ zipWith (==) taillist headlist


-- binaries
-- code xs = read xs :: Integer
-- code :: Num a => [a] -> [a]
-- code xs = foldl (\acc x -> (acc - (mod acc 2)) : x) i [2, 2..]
    -- where i = read xs :: Integer

-- codewars
findNextSquare :: Integer -> Integer
findNextSquare n 
    | ispefect truen = truncate $ head $ filter ispefect [truen + 1..]
    | otherwise = -1
    where truen = fromInteger n
-- ispefect :: Integer -> Bool
ispefect x = fromIntegral (truncate . sqrt $ x)^2 == x   

rowSumOddNumbers :: Int -> Integer
rowSumOddNumbers x = sum $ take x $ drop (sum [1..x-1]) [1, 3..]


-- https://www.codewars.com/kata/546e2562b03326a88e000020/train/haskell
squareDigit :: Int -> Int
squareDigit it = read $ proc it :: Int 
   where proc = concatMap (show . (^2)) . intToList

intToList :: Int -> [Int]
intToList = everyToDigit . map show . show
    where everyToDigit  = map (\x -> digitToInt (read x :: Char)) 
````