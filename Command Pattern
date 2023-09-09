// 指令模式
using System.Collections;
using System.Collections.Generic;
using UnityEngine;

#region 指令
public abstract class Command
{
    public abstract void Excute(GameObject gameObject, float input);
}
public class MoveForward : Command
{
    public override void Excute(GameObject gameObject, float input)
    {
        gameObject.transform.position += new Vector3(0, 0, input);
    }
}
public class MoveBack : Command
{
    public override void Excute(GameObject gameObject, float input)
    {
        gameObject.transform.position += new Vector3(0, 0, input);
    }
}
public class MoveLeft : Command
{
    public override void Excute(GameObject gameObject, float input)
    {
        gameObject.transform.position += new Vector3(input, 0, 0);
    }
}
public class MoveRight : Command
{
    public override void Excute(GameObject gameObject, float input)
    {
        gameObject.transform.position += new Vector3(input, 0, 0);
    }
}
#endregion

public class 指令模式 : MonoBehaviour
{
    MoveForward moveForward;
    MoveBack moveBack;
    MoveLeft moveLeft;
    MoveRight moveRight;

    Direction orientation;
// 命令的初始化
    void Start()
    {
        moveForward = new MoveForward();
        moveBack = new MoveBack();
        moveLeft = new MoveLeft();
        moveRight = new MoveRight();
    }
    
    enum Direction
    {
        Forward,Backward,Left,Right
    }

    void Update()
    {
       
        if (Input.GetKeyDown(KeyCode.W))
        {
            moveForward.Excute(gameObject, 1);
            orientation = Direction.Forward;
        }
        if (Input.GetKeyDown(KeyCode.S))
        {
            moveBack.Excute(gameObject, -1);
            orientation = Direction.Backward;
        }
        if (Input.GetKeyDown(KeyCode.A))
        {
            moveLeft.Excute(gameObject, -1);
            orientation = Direction.Left;
        }
        if (Input.GetKeyDown(KeyCode.D))
        {
            moveRight.Excute(gameObject, 1);
            orientation = Direction.Right;
        }
//撤销上一步操作
        if(Input.GetKeyDown(KeyCode.Z))
        {
            switch (orientation)
            {
                case Direction.Forward:
                    moveBack.Excute(gameObject, -1);
                    orientation = Direction.Forward;
                    break;
                case Direction.Backward:
                    moveForward.Excute(gameObject, 1);
                    orientation = Direction.Forward;
                    break;
                case Direction.Left:
                    moveRight.Excute(gameObject, 1);
                    orientation = Direction.Right;
                    break;
                case Direction.Right:
                    moveLeft.Excute(gameObject, -1);
                    orientation = Direction.Left;
                    break;
                default:
                    break;
            }

        }
    }
}
