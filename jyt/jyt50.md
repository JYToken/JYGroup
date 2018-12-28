# JYT 的算法

1. 初始价格 0.0000001 ETH / JYT

2. ethereumToTokens_

   ```
           uint256 _tokenPriceInitial = tokenPriceInitial_ * 1e18;
           uint256 _tokensReceived = 
            (
               (
                   // underflow attempts BTFO
                   SafeMath.sub(
                       (sqrt
                           (
                               (_tokenPriceInitial**2)
                               +
                               (2*(tokenPriceIncremental_ * 1e18)*(_ethereum * 1e18))
                               +
                               (((tokenPriceIncremental_)**2)*(tokenSupply_**2))
                               +
                               (2*(tokenPriceIncremental_)*_tokenPriceInitial*tokenSupply_)
                           )
                       ), _tokenPriceInitial
                   )
               )/(tokenPriceIncremental_)
           )-(tokenSupply_);
   ```

3. tokensToEthereum_

   ```
           uint256 tokens_ = (_tokens + 1e18);
           uint256 _tokenSupply = (tokenSupply_ + 1e18);
           uint256 _etherReceived =
           (
               // underflow attempts BTFO
               SafeMath.sub(
                   (
                       (
                           (
                               tokenPriceInitial_ +(tokenPriceIncremental_ * (_tokenSupply/1e18))
                           )-tokenPriceIncremental_
                       )*(tokens_ - 1e18)
                   ),(tokenPriceIncremental_*((tokens_**2-tokens_)/1e18))/2
               )
           /1e18);
   ```



