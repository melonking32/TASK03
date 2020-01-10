# TASK03队列
```C++
void outputFromHoldingTrack()
{
 track[itsTrack].pop();
 cout<<"Move car"<<smallestCar<<"from holding track"<<itsTrack<<"to output track"<<endl;

 smallestCar=numberOfCars+2;
 for(int i=1;i<=numberOfTracks;i++)
 {
     if(!track[i].empty()&&track[i].front()<smallestCar)
     {
         smallestCar=track[i].front();
         itsTrack=i;
     }
 }
}

bool putInHoldingTrack(int c)
{
int bestTrack=0,bestLast=0;
//扫描缓冲轨道
for(int i=1;i<=numberOfTracks;i++)
    if(!track[i].empty())
    {
        int lastCar=track[i].back();
        if(c>lastCar&&lastCar>bestLast)
        {
          bestLast=lastCar;
          bestTrack=i;
        }
    }
    else
        if(bestTrack==0)
            bestTrack=i;
if(bestTrack==0)
    return false;

track[bestTrack].push(c);
cout<<"Move car"<<c<<"from input track"<<"to holding track"<<bestTrack<<endl;

if(c<smallestCar)
{
    smallestCar=c;
    itsTrack=bestTrack;
}
return true;

}
