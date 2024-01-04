#Your task is to complete this function
#Function should return complete string
def encode(arr):
    # Code here
    if len(arr)<1:
        return arr
    ans=""
    char=arr[0]
    count=1
    for i in range(1,len(arr)):
        if char!=arr[i]:
            ans+=char+str(count)
            char=arr[i]
            count=1
        elif char==arr[i]:
            count+=1
    ans+=char+str(count)
    return ans

