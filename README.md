# UIKit.ControllerTransition

```Swift

class ViewController: UIViewController {

    private var delegate1: TransitioningDelegate?

    @IBAction func openButtonTapped(_ sender: Any) {
        let controller = DetailViewController()
        delegate1 = TransitioningDelegate()

        controller.modalPresentationStyle = .custom
        controller.transitioningDelegate = delegate1

        present(controller, animated: true)
    }
}

class TransitioningDelegate: NSObject, UIViewControllerTransitioningDelegate {
    
    func presentationController(forPresented presented: UIViewController, 
                                presenting: UIViewController?, source: UIViewController) 
                                -> UIPresentationController? {
        return PresentationController(presentedViewController: presented, 
                                      presenting: presenting)
    }
}

class PresentationController: UIPresentationController {

    override var frameOfPresentedViewInContainerView: CGRect {
        return CGRect(x: 0,
                      y: containerView!.bounds.height * CGFloat(2.0 / 3.0),
                      width: containerView!.bounds.width,
                      height: containerView!.bounds.height * CGFloat(1.0 / 3.0))
    }
}

```

![image](https://user-images.githubusercontent.com/15805568/170802354-4ae8db34-ee98-46cf-9018-c1bdf0d11b93.png)

